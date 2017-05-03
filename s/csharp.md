C\#
===

From the [C# Online](https://web.archive.org/web/20100209182834/http://en.csharp-online.net/Main%28%29) wiki page [ASP.NET Security Hacks--Avoiding SQL Injection](https://web.archive.org/web/20121230034810/http://en.csharp-online.net/ASP.NET_Security_Hacks%E2%80%94Avoiding_SQL_Injection)


    SqlCommand userInfoQuery = new SqlCommand(
        "SELECT id, name, email FROM users WHERE id = @UserName",
        someSqlConnection);

    SqlParameter userNameParam = userInfoQuery.Parameters.Add("@UserName",
        SqlDbType.VarChar, 25 /* max length of field */ );

    // userName is some string valued user input variable
    userNameParam.Value = userName;

Or simpler:


    String username = "joe.bloggs";
    SqlCommand sqlQuery = new SqlCommand("SELECT user_id, first_name,last_name FROM users WHERE username = ?username",  sqlConnection);
    sqlQuery.Parameters.AddWithValue("?username", username);
