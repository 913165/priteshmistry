## Welcome to GitHub Pages Pritesh Mistry

You can use the [editor on GitHub](https://github.com/913165/priteshmistry/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

# Kafka Docker setup URL

[I'm an inline-style link](https://www.google.com)

[https://docs.confluent.io/platform/current/quickstart/ce-docker-quickstart.html](https://docs.confluent.io/platform/current/quickstart/ce-docker-quickstart.html)

# mysql docker setup with remote connection with root user

make sure to open port in cloud
docker run --name=mk-mysql -p3306:3306 -v mysql-volume:/var/lib/mysql -e MYSQL_ROOT_HOST=% -e MYSQL_ROOT_PASSWORD=root -d mysql/mysql-server:8.0.20
