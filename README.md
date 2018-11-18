# Presto Sqlserver Plugin

This is a plugin for Presto that allow you to use Sqlserver Jdbc Connection using the [jtds driver](http://jtds.sourceforge.net/) which supports some types of connections with SQL Server that the standard microsoft jdbc driver does not (e.g. domain logins).

The code is mainly inherited from [lotuc/presto-oracle](https://github.com/lotuc/presto-oracle) which is forked from [marcelopaesrech/presto-oracle](https://github.com/marcelopaesrech/presto-oracle)

## Connection Configuration

Create new properties file inside etc/catalog dir:

    connector.name=jtds-sqlserver
    connection-url=jdbc:jtds:sqlserver://ip:port;databaseName=MYDBNAME;domain=MYDOMAIN;useNTLMv2=true;
    connection-user=myusername
    connection-password=mypassword

## Building Presto JTDS SQL Server JDBC Plugin

    gradle build

## Plugin installation

First build the plugin.

Then create a dir inside plugin dir called sqlserver. To make it easier you could copy mysql dir to sqlserver and remove the mysql-connector and prestodb-mysql jars. Finally put the prestodb-sqlserver in plugin/sqlserver folder. Here is the sptes:

    cd $PRESTODB_HOME
    cp -r plugin/mysql plugin/jtds-sqlserver
    rm plugin/sqlserver/mysql-connector*
    rm plugin/sqlserver/presto-mysql*
    cp $SQLSERVER_PLUGIN_REPO/lib/* plugin/jtds-sqlserver
    cp $SQLSERVER_PLUGIN_REPO/build/libs/presto-jtds-sqlserver*.jar plugin/jtds-sqlserver

