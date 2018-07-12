# MySQL Error Codes

This project intends to provide fuller error messaging for MySQL error messages.

## Sample Use

### OLD Error Messaging

Normally, in PHP and MySQL, the only error information you can get is...

	$db_link = new mysqli($this->hostname,$this->username,$this->password);
	print($db_link->connect_errno . " : " . $db_link->connect_error);

This will only give output like...

	13236 : Message: Newly created data directory SOMEDIRECTORY is unusable. You can safely remove it.

### NEW Error Messaging

But with MySQLErrorCodes...

	$db_link = new mysqli($this->hostname,$this->username,$this->password);
	print($db_link->connect_errno . " : " . $db_link->connect_error);
	
	$mysql_error = new MySQLErrorCode();
	$error_codes = $mysql_error->ErrorCodes();
	
	print_r($error_codes[13236]);
	
And this will give the full output of...

	13236 : Message: Newly created data directory SOMEDIRECTORY is unusable. You can safely remove it.

	'13236' => [
		'error_code' => '13236',
		'internal_code' => 'ER_DATA_DIRECTORY_UNUSABLE',
		'message_template' => 'Message: Newly created data directory %s is unusable. You can safely remove it.',
		'sql_state' => 'HY000',
		'version_information' => 'ER_DATA_DIRECTORY_UNUSABLE was added in 8.0.13.'
	],
