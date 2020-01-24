# casbin-sqlx-adapter
### This is fork of the original project [casbin-sqlx-adapter](https://github.com/memwey/casbin-sqlx-adapter)

sqlx adapter for Casbin https://github.com/casbin/casbin

Based on [sqlx](https://github.com/jmoiron/sqlx), and tested in [MySQL](https://github.com/go-sql-driver/mysql) and [Postgres](https://github.com/lib/pq).

## Installation

    go get github.com/mef13/casbin-sqlx-adapter

## Usage example

```go
opts := &AdapterOptions{
    DriverName: "mysql",
    DataSourceName: "root:1234@tcp(127.0.0.1:3306)/yourdb",
    TableName: "casbin_rule",
    // or reuse an existing connection:
    // DB: myDBConn,
}

a := NewAdapterFromOptions(opts)
// Casbin v2 may return an error
e, err := casbin.NewEnforcer("examples/rbac_model.conf", a)
if err != nil {
    panic(err)
}
```

## Notice

The v2 version of Casbin has some break change, check for the [detail](https://github.com/casbin/casbin/releases/tag/v2.0.0). If you are still using v1 version, use `0.1.x` of this project.

The implement is kind of different from the [official one](https://casbin.org/docs/en/adapters). In this implement you should create the database and table on your own.

In my opinion, in a general PRODUCTION environment, the business code can rarely create a database, create a table or drop a table.

## Thank

Thanks to [casbin-sqlx-adapter](https://github.com/memwey/casbin-sqlx-adapter) for his original project.

## License

This project is under Apache 2.0 License. See the [LICENSE](LICENSE) file for the full license text.
