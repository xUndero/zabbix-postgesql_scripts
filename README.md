# zabbix-postgesql_scripts
```
update hstgrp set name = REPLACE(name, 'OLD', 'NEW') where name like '%OLD%';
update usrgrp set name = REPLACE(name, 'OLD', 'NEW') where name like '%OLD%';
update actions set name = REPLACE(name, 'OLD', 'NEW') where name like '%OLD%';
update hosts set name = REPLACE(name, 'OLD', 'NEW') where name like '%OLD%';
update sysmaps set name = REPLACE(name, 'OLD', 'NEW') where name like '%OLD%';
update sysmaps_elements set label  = REPLACE(label, 'OLD', 'NEW') where label like '%OLD%';

select imageid from images where name like '%outer%';
select iconid_off,label from sysmaps_elements where iconid_off in (select imageid from images where name like '%outer%') and label like '%ciscoPhysicalModelName%';
update sysmaps_elements set label = REPLACE(label, 'ciscoPhysicalModelName', 'system.hw.model') where iconid_off in (130,155,193) and label like '%ciscoPhysicalModelName%';

select name from hosts where hostid in (select hostid from items where itemid in (select itemid from item_condition where macro='{#IFNAME}' AND value like '%^%'));
```
