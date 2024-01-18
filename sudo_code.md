1. Open the Socks Tunnel ---- Localhost
2. Run the select query from the Jumphop where tower connects and connect to dsmadmc and collect the data on exel
   ----  Jumphop
3. Once the data is collected we get NODE_NAME , SCHEDULE_NAME , Server_Name , TCP_NAME & PLATFORM_NAME to excel.   ----  Jumphop
4. Read the csv from jumphop read_csv and register the data. ----  Jumphop
5. We have to iterate the tcpnames to next play as the hosts and each line when the TCP name matches and run the CE  role with the input values of CSV if it's windows run one play or else run other plat with custom cred


 We can run this command on the Jumpserver and collect the data on excel


select SUBSTR(CHAR(s.server_name),1,14) as TSM_SERVER ,e.NODE_NAME,e.schedule_name,(select tcp_name from nodes n where e.node_name=n.node_name),(select PLATFORM_NAME from nodes n1 where e.node_name=n1.node_name) from events e,status s where ( e.STATUS='Failed' or e.STATUS='Missed' ) and (e.COMPLETED>=(current_timestamp - 24 hour) ) and ( e.schedule_name not like '@%' and e.schedule_name like 'ARC%')



We can read this excel and delegate the CE role




