## Sample Installation

### Kafka Docker setup URL
- [https://docs.confluent.io/platform/current/quickstart/ce-docker-quickstart.html](https://docs.confluent.io/platform/current/quickstart/ce-docker-quickstart.html)

### maven dependencies

```maven
               <dependency>
			<groupId>org.apache.kafka</groupId>
			<artifactId>kafka-clients</artifactId>
			<version>2.7.0</version>
		</dependency>
 ```
 
### Kafka simple Prducer

 ```java
   import java.util.Properties;
	import org.apache.kafka.clients.producer.Producer;
	import org.apache.kafka.clients.producer.KafkaProducer;
	import org.apache.kafka.clients.producer.ProducerRecord;
	public class KafkaSimpleProducer {
		public static void main(String[] args) throws Exception {
			String topicName = "test1";
			Properties props = new Properties();
			props.put("bootstrap.servers", "138.91.78.226:9092");
			props.put("acks", "all");
			props.put("key.serializer", "org.apache.kafka.common.serialization.StringSerializer");
			props.put("value.serializer", "org.apache.kafka.common.serialization.StringSerializer");
			Producer<String, String> producer = new KafkaProducer<String, String>(props);
			for (int i = 0; i < 10; i++)
				producer.send(new ProducerRecord<String, String>(topicName, Integer.toString(i), Integer.toString(i)));
			System.out.println("Message sent successfully");
			producer.close();
		}
	 }
    }
```

### Kafka simple Consumer

 ```java
    public class KafkaSimpleConsumer {
	public static void main(String[] args) throws Exception {
		// Kafka consumer configuration settings
		String topicName = "test1";
		Properties props = new Properties();
		props.put("bootstrap.servers", "138.91.78.226:9092");
		props.put("group.id", "test");
		props.put("key.deserializer", "org.apache.kafka.common.serialization.StringDeserializer");
		props.put("value.deserializer", "org.apache.kafka.common.serialization.StringDeserializer");
		KafkaConsumer<String, String> consumer = new KafkaConsumer<String, String>(props);
		consumer.subscribe(Arrays.asList(topicName));
		System.out.println("Subscribed to topic " + topicName);
		int i = 0;

		while (true) {
			ConsumerRecords<String, String> records = consumer.poll(100);
			for (ConsumerRecord<String, String> record : records)
				System.out.printf("offset = %d, key = %s, value = %s\n", record.offset(), record.key(), record.value());
		}
	}
}

 ```

### mysql docker setup with remote connection with root user

- make sure to open port in cloud
- docker run --name=mk-mysql -p3306:3306 -v mysql-volume:/var/lib/mysql -e MYSQL_ROOT_HOST=% -e MYSQL_ROOT_PASSWORD=root -d mysql/mysql-server:8.0.20

### Oracle docker setup with remote connection with system user

- make sure to open port in cloud
- docker run -d -p 1521:1521 -e ORACLE_ALLOW_REMOTE=true oracleinanutshell/oracle-xe-11g
- username : system
- password : oracle
