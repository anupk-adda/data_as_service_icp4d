# data_as_service_icp4d
sample implementation of data as a service on IBM Cloud Private for Data Platform

Step 1. 
+++++++++++++++
import the project to any IBM cloud pak for data  instance ver 1.1 /watson studio  2.0 onwards.


Step 2.
+++++++++++++++++++
modify the daassetup.py  dbConnection() function to point to your database or data virtualization isntance.

def dbConnection():
  dsn_database = "BLUDB"
  dsn_hostname = "dashdb-entry-yp-syd01-01.services.au-syd.bluemix.net"
  dsn_port = "50000"
  dsn_uid = "dash33171"
  dsn_pwd = "_Qlx0fH6_R"
  
 

Step 3.
 +++++++++++++++++++++
 add function and define the input and output variables.
 
  def getCustomerDetails(custkey):
  outf='{"col1":"c_first_name","col2":"C_LAST_NAME","col3":"c_email_address"}'
  outputColumn= parseOutput(outf)
  #print(outputColumn)
  inputp={"tableName": "customer", "filterCol": "c_customer_sk", "filterValue": str(custkey)}
  if (parseInput(inputp) ==1 ):
    print("input error please try with correct filter critria")
  else :
    return executeQuery(inputp,outputColumn) 
