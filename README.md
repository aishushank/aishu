# aishu
<?php 
ob_start();
ini_set("log_errors", 1);
ini_set("error_log", "/tmp/php-error.log");
require("dbcon.php");
require("functions.php");
if((isset($_COOKIE['BrCode'])) && (isset($_COOKIE['UsrId']))) 
{
  $BrCode=$_COOKIE['BrCode'];
  $UsrId=$_COOKIE['UsrId'];
  $q1=mysql_query("SELECT usr_check from b0201 where UserCode='".$UsrId."' and BrCode = '".$BrCode."' and status='1'") or die(errorLogin(mysql_error())."::||::"."0");
  $q1=mysql_fetch_array($q1);
  errorLogin("Inside Loop: Module : Index page. User='".$UsrId."' logined with '".$q1[0]."'");
  echo $q1[0];
}
else
{
  header("Location:loginmain.php");
}
mysql_close($con);
ob_flush();
?>
