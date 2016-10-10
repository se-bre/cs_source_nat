## Cloudstack - change source NAT IP

you can't change the source NAT ip of the network with the API/UI

If you want to change you need to do the following:  

1.) Acuire another public ip to the network  
2.) Stop the router  
3.) login to your Database  
4.) edit the user_ip_address table, source_nat column  
  - get the id of the ip  

        select * from user_ip_address where public_ip_address="<public_IP>" \G;

  - change the source_nat column

        update user_ip_address set source_nat='1' where id='<ID>';

  do this for both ip's - set the old one to "0" and the new to "1"

5.) restart the network - with "Clean up" flag!  

---
