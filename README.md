# spring-cloud-config-demo

# Read Me First

The following was discovered as part of building this project:

* The original package name 'com.gautamgupta.spring-cloud-config-demo' is invalid and this project uses '
  com.gautamgupta.springcloudconfigdemo' instead.

# Getting Started

Step 1:
create a repo and all required properties file as per your need
for example: https://github.com/gautam-gupta-se/ms-config-repo
after runnig the application u can verify the config details

http://localhost:9000/config-server/default

{"name":"config-server","profiles":["default"],"label":null,"version":"b7619e589a8672a7847298a89412f4843da793ae","
state":null,"
propertySources":[{"name":"https://github.com/gautam-gupta-se/ms-config-repo/application.properties",
"source":{"spring.datasource.driverClassName":"com.mysql.jdbc.Driver",
"spring.datasource.username":"root",
"spring.datasource.password":"root",
"spring.jpa.hibernate.ddl-auto":"update",
"newprop":"my new property"
}}]
}

-----------------------------------------------------------------------
http://localhost:9000/CartMS/default
{"name":"CartMS","profiles":["default"],"label":null,"version":"b7619e589a8672a7847298a89412f4843da793ae","state":null,"
propertySources":[{"name":"https://github.com/gautam-gupta-se/ms-config-repo/CartMS.properties",
"source":{"spring.datasource.url":"jdbc:mysql://localhost/inventry_cart"}},
{"name":"https://github.com/gautam-gupta-se/ms-config-repo/application.properties",
"source":{"spring.datasource.driverClassName":"com.mysql.jdbc.Driver",
"spring.datasource.username":"root","spring.datasource.password":"root",
"spring.jpa.hibernate.ddl-auto":"update",
"newprop":"my new property"
}}]
}
----------------------------------------------------------------------
{"name":"PaymentMS","profiles":["default"],"label":null,"version":"b7619e589a8672a7847298a89412f4843da793ae",
"state":null,
"propertySources":[{"name":"https://github.com/gautam-gupta-se/ms-config-repo/PaymentMS.properties",
"source":{"spring.datasource.url":"jdbc:mysql://localhost/inventry_payment"}},
{"name":"https://github.com/gautam-gupta-se/ms-config-repo/application.properties",
"source":{"spring.datasource.driverClassName":"com.mysql.jdbc.Driver",
"spring.datasource.username":"root",
"spring.datasource.password":"root",
"spring.jpa.hibernate.ddl-auto":"update",
"newprop":"my new property"
}}]
}

------------------------------------------------------------------------
now you can get required centralized properties from config server using below configuration
for example in your repo there in PaymentMS.properties file it will get all specific config along with
apllication.properties and yml
add dependency " spring-cloud-starter-config and spring-boot-starter-actuator "
add these properties in your application.properties:
spring.application.name=PaymentMS
server.port=9001
spring.jackson.default-property-inclusion: NON_NULL
spring.config.import=optional:configserver:http://localhost:9000


