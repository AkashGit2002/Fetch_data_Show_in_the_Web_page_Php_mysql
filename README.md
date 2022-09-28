# Fetch_data_Show_in_the_Web_page_Php_mysql
Fetch_data_Show_in_the_Web_page_Php_mysql


#Tech-Stach: PHP & MYSQL

<?php

$user='root';
$password='';

$server='localhost:3306';

$database='test';

$conn=new mysqli($server,$user,$password,$database);

if($conn->connect_error){
 	die('Connect Error (' .
	$conn->connect_errno . ') '.
	$conn->connect_error);


}
if(isset($_GET['fname'])){
	$ename=$_GET['fname'];
}
else{
	echo 'Error';
}



$sql="select * from emp where first_name='$ename'";
try{
$result=$conn->query($sql);
if(mysqli_num_rows($result)==0){
	echo "error".$result;
}

}
catch(Exception $e){
echo $e->errorMessage();
}

$conn->close();

?>

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta http-equiv="X-UA-Compatible" content="IE=edge">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Employee Records Details</title>
	
		<style>
		table {
			margin: 0 auto;
			font-size: large;
			border: 1px solid black;
			border-collapse: collapse;
		}

		h1 {
			text-align: center;
			color: #006600;
			font-size: xx-large;
			font-family: 'Gill Sans', 'Gill Sans MT',
			' Calibri', 'Trebuchet MS', 'sans-serif';
		}

		td {
			background-color: #E4F5D4;
			border: 1px solid black;
		}

		th,
		td {
			font-weight: bold;
			border: 1px solid black;
			padding: 10px;
			text-align: center;
		}

		td {
			font-weight: lighter;
		}
	
	</style>
</head>
<body>
<section>
	<h1>Employee Details</h1>
	<table>
		<tr>
			<th>EmployeeId</th>
			<th>Employee's First Name</th>
			<th>Employee's Last Name</th>
			<th>Employee's Compansation</th>
			<th>Employee's DateOfJoining</th>
			<th>Employee's Department</th>
        </tr>
		<?php 
			
			while($rows = $result ->fetch_assoc())
			{
		?>
		<tr>
			<td><?php echo $rows['empid']; ?></td>
			<td><?php echo $rows['first_name']; ?></td>
			<td><?php echo $rows['last_name']; ?></td>
			<td><?php echo $rows['salary']; ?></td>
			<td><?php echo $rows['doj']; ?></td>
			<td><?php echo $rows['dept']; ?></td>
		</tr>
		<?php
			}
			?>
        </tr>
    </table>
</section>
<table>

</table>
	
</body>
</html>



<?
