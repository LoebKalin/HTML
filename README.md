### if username already exist check from radcheck

`const acc = await pool.query("select * from radcheck where username=$1", [ username ]);`

### insert into table radcheck

`const newAcc = await pool.query( "insert into radcheck(username, attribute,op,value) VALUES($1,$2,$3,MD5($4)) RETURNING *", [username, attributeMD5, op, password] );`

### insert into table RAD_GROUP_CHECK

`const rad = await pool.query( "insert into radgroupcheck(groupname, attribute, op, value) VALUES($1, $2, $3, $4) RETURNING *", [sim_Name, attributeSim, op, sim] );`

`const rad = await pool.query( "insert into radgroupcheck(groupname, attribute, op, value) VALUES($1, $2, $3, $4) RETURNING *", [exp_or_period_Name, attri, op, due] );`

### insert into radusergroup

`const radgroupcheck = await pool.query( "insert into radusergroup(username, groupname, priority) VALUES($1, $2, $3) RETURNING *", [username, sim_Name, priority] );`

`const radusergroup = await pool.query( "insert into radusergroup(username, groupname, priority) VALUES($1, $2, $3) RETURNING *", [username, exp_or_period_Name, priority] );`
