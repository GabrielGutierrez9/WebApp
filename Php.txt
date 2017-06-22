<!DOCTYPE html>

<!-- this form processes the information from the login html -->

<html>
	<head>
		<meta charset = "utf-8">
		<title> Verifiy Login Details</title>
		<style type = "text/css">
		body 
		{
			font-family: sans-serif;
			background-color: lightyellow;
		}

		table
		{
			background-color: lightblue;
			border-collapse: collapse;
			border: 1px solid gray;
		}
		
		</style>
	</head>
	<body>
	<?php
	$UName = $POST["uname"];
	$Pword = $POST["pword"];
	
	//select query
	$query = "SELECT Uname FROM Users WHERE Uname = '". $Uname "AND Pword = '" $Pword."';";
	
	//Connect to DB
	if(!($database = mysql_connect("192.168.3", "gabriel", "1234")))
	die("Unable to connnect to database </body></html>");
	
	//open Users DB
	if(!mysql_select_db("Users", $database))
	die("Cannot open Users database </body></html>");

	//handle username not found
	if(!($check = mysql_query( $query, $database)))
	
		print("<p>Incorrect username and or password!</p>");
		die(mysql_error() . "</body><html>");
	
	else
	{
		print("<p> Success!</p>");
		$check = mysql_query( $query, $database);
	}
	
	//close db
	mysql_close($database);
	?><!-- end of PHP script -->
	<table>
		<caption> Account Details </caption>
	<?php
	//obtain record
	while ($row = mysql_fetch_row($check)
	{
		//build table 
		print("<tr>");
	foreach( $row as $key => $value)
		print( "<td>$value</td>");
		print("</tr>");
	}//end while loo
	?><--! end PHP script -->

	</body>
</html>
	
		


	    	
	