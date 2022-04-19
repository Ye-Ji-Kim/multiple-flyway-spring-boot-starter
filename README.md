# Flyway Multiple DataSource Configuration

 This project provides flyway auto-configuration for multiple data sources

# How to Use

## Add Dependency

Add in your `build.gradle` the following:

```groovy
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```
```groovy
dependencies {
        implementation 'com.github.Ye-Ji-Kim:multiple-flyway-spring-boot-starter:1.0.0'
}

```

## Set Properties
For each database, you need to configure properties in `application.yaml` as follows:
```yaml
multiple-flyway:
  enabled: true
  properties:
    - data-source: dataSource1
      locations: classpath:db/migration/db1
      baseline-on-migrate: true
      ...
      
    - data-source: dataSource2
      locations: classpath:db/migration/db2
      baseline-on-migrate: true
      ...
```
Before you use this auto-configuration, you need to configure `DataSource` Bean.

#### enabled
Default is `true`. 
So if you add this dependency, the multiple configuration for flyway will run automatically.
To disable this auto-configuration, set `multiple-flyway.enabled` to `false`.

#### properties
You can configure properties for each database in List type.
You can use almost all properties offered by Spring Boot FlywayAutoConfiguration.
- **data-source** : `DataSource` bean name
