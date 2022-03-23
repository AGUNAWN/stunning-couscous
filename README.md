# stunning-couscous
Operation - Couscous 
proc sql noprint;
create table match_db1 as 
select * , geodist (a.Y,a.X,b.lat,b.long,'M') as distance
from work.data1 as a left join work.data2 as b
on (a.PSAP=b.DPphone_PU)
and a.hour_start=b.hour_start10
and (COMPGED(put(a.streetaddress,$42.), put(b.street_address,$42.)) le 590))
order by a.Incident
;
quit;
