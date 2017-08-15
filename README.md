# OCIGO

An wrapper in GO for OCILIB https://github.com/vrogier/ocilib an excelent wrapper for OCI from Oracle.

Hope be the one-to-one in go lib for c lib.

Many tips & tricks were obtained from https://github.com/tgulacsi/gocilib an driver compatible with database/sql.

## Examples

Example of a minimal OCIGO program

```GO

import (
  "fmt"
   oci "github.com/jmptrader/ocigo"
)


 
func main()
{

    oci.Initialize( oci.NULL , oci.NULL, oci.OCI_ENV_DEFAULT)
 
    cn := oci.ConnectionCreate("db", "usr", "pwd", oci.OCI_SESSION_DEFAULT)     // oci.Connection
    st := oci.StatementCreate(cn)                                               // oci.Statement
 
    oci.ExecuteStmt(st, "select intcol, strcol from table")
 
    rs := oci.GetResultset(st)   // oci.Resultset
 
    for oci.FetchNext(rs) > 0 {
        fmt.Println("%i - %s", oci.GetInt(rs, 1), oci.GetString(rs,2) )
    }
 
    oci.Cleanup();
 
}
```



  


