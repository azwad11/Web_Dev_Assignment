<?php

$servername = "localhost";
$username = "root";
$password = "";
$dbname = "formdb";

$conn = new mysqli($servername, $username, $password, $dbname);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

// Get form data
$first_name = $_POST['first_name'];
$last_name = $_POST['last_name'];
$email = $_POST['email'];
$phone_number = $_POST['phone_number'];
$message = $_POST['message'];

// SQL query to insert data
$sql = "INSERT INTO contacts (first_name, last_name, email, phone_number, message)
        VALUES ('$first_name', '$last_name', '$email', '$phone_number', '$message')";

if ($conn->query($sql) === TRUE) {
    echo "";
    header("Location: index.html");
} 
else {
    echo "Error: " . $sql . "<br>" . $conn->error;
}

$conn->close();
?>
