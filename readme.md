#### create table team_b (
#### id serial primary key,
###### ## name VARCHAR (255) not null,
#### email VARCHAR (255) unique not null,
#### age integer not null,
#### created_on TIMESTAMP not null,
#### foreign key (id) references role(id)
#### );

#### insert into team (name, email, age, created_on) values ('Javier', 'javier.bravoz@mail.udp.cl', '33', now());
#### insert into team (name, email, age , created_on) values ('Catalina', 'cata@gmail.com', '32', now());


#### select s.id, s.age, s.name from team s;

#### insert into team (name, email, age,  created_on) values ('Joaquin', 'j',  '33', now());
#### insert into team (name, email, age , created_on) values ('Juan', 'Ju', '30',  now());
#### insert into team (name, email, age,  created_on) values ('Marcos', 'M', '33',  now());
#### insert into team (name, email, age,  created_on) values ('Marcela', 'Ma', '5',  now());
#### insert into team (name, email, age,  created_on) values ('Pedro', 'Pe', '33',  now());
#### insert into team (name, email, age , created_on) values ('Paulina', 'Pa', '15',  now());

#### select * from team s where s.name like 'J%';

#### update team set age = '40' where id = '4';
#### update team set email = 'pedro@gmail.com' where email = 'Pe';
#### update team set id = '2' where id = '5';

#### alter table team  add role VARCHAR(15);

#### update  team set role = 'seller' where name = 'Joaquin';
#### update  team set role = 'coach' where name = 'Marcos';
#### update  team set role = 'seller' where name = 'Marcela';
#### update team set role = 'coach' where name = 'Pedro';
#### update team set role = 'admin' where name = 'Paulina';
#### update team set role = 'coach' where name = 'Juan';
#### update team set role = 'seller' where name = 'Catalina';
#### update team set role = 'boss' where name = 'Javier';
#### update team set email = 'joaquin@gmail.com' where name = 'Joaquin';
#### update team set email = 'marcos@gmail.com' where name = 'Marcos';
#### update team set email = 'marcela@gmail.com' where name = 'Marcela';
#### update team set email = 'paulina@gmail.com' where name = 'Paulina';
#### update team set email = 'juan@gmail.com' where name = 'Juan';

#### create table role (
#### id serial primary key,
#### name VARCHAR (15) not null,
#### description text not null
#### );

#### insert into role (name, description) values ('seller', 'sellers find and receive customers bringing information and guiding them through the buying process');
#### insert into role (name, description) values ('coach', 'coaches must train our customers physically and mentally so they would improve their lifestyles using our products as tools');
#### insert into role (name, description) values ('admin', 'the admin coordinates the team to make sure everything is working correctly');
#### insert into role (name, description) values ('supervisor', 'the hand');
#### insert into role (name, description) values ('rookie', 'the servant');

#### select s.description from role s; 
#### select * from role s;

#### alter table team drop column role_id;
#### alter table team add role_id int;

#### update team set role_id = '1' where name = 'Joaquin';
#### update team set role_id = '2' where name = 'Marcela';
#### update team set role_id = '3' where name = 'Paulina';
#### update team set role_id = '2' where name = 'Juan';
#### update team set role_id = '4' where name = 'Javier';
#### update team set role_id = '2' where name = 'Pedro';
#### update team set role_id = '1' where name = 'Marcos';
#### update team set role_id = '1' where name = 'Catalina';

#### alter table team add constraint fk_id_role foreign key (role_id) references role(id);

#### select s.* from team s
#### join role sc on sc.id = s.role_id where sc."name" = 'coach';

#### #### create or replace procedure promoteTeamMember(team_id int)
#### language plpgsql
####  $$
#### begin 
#### 	--promote every coach to  supervisor
#### 	update team 
#### 	set role_id = 5
#### 	where id = team_id;	
#### 	commit;
#### end;$$

#### call promoteTeamMember(6);
#### call promoteTeamMember(8);
#### call promoteTeamMember(9);

#### create or replace procedure degradeTeamMember(team_id int)
#### language plpgsql
#### as $$
#### begin 
#### 	--promote every coach to  supervisor
#### 	update team 
#### 	set role_id = 6
#### 	where id = team_id;	
#### 	commit;
#### end;$$

#### call degradeTeamMember(2);
#### call degradeTeamMember(8);
