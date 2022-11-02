# Base de datos: Blog

### Link a DBDiagram

[Blog]

## Comandos SQL

````sql

CREATE TABLE "author" (
  "id" SERIAL PRIMARY KEY,
  "name" varchar,
  "nickname" varchar NOT NULL
);

CREATE TABLE "users" (
  "id" SERIAL PRIMARY KEY,
  "name" varchar,
  "lastname" varchar,
  "nickname" varchar,
  "email" varchar NOT NULL,
  "password" varchar NOT NULL
);

CREATE TABLE "usersComments" (
  "id" SERIAL PRIMARY KEY,
  "userId" int NOT NULL,
  "commentsId" int NOT NULL
);

CREATE TABLE "posts" (
  "id" SERIAL PRIMARY KEY,
  "title" varchar NOT NULL,
  "description" text NOT NULL,
  "authorId" int NOT NULL,
  "tagId" int
);

CREATE TABLE "tags" (
  "id" SERIAL PRIMARY KEY,
  "nameTag" varchar NOT NULL
);

CREATE TABLE "comments" (
  "id" SERIAL PRIMARY KEY,
  "comment" text NOT NULL,
  "postId" int NOT NULL
);

ALTER TABLE "usersComments" ADD FOREIGN KEY ("userId") REFERENCES "users" ("id");

ALTER TABLE "posts" ADD FOREIGN KEY ("authorId") REFERENCES "author" ("id");

ALTER TABLE "usersComments" ADD FOREIGN KEY ("commentsId") REFERENCES "comments" ("id");

ALTER TABLE "posts" ADD FOREIGN KEY ("tagId") REFERENCES "tags" ("id");

ALTER TABLE "comments" ADD FOREIGN KEY ("postId") REFERENCES "posts" ("id");

insert into author ("name", "nickname")
values ('Javier Hernandez', 'Chicharito'), ('Jorge Gomez', 'JorgeG');

insert into users ("name", "lastname", "nickname", "email", "password")
values ('Diego', 'Silva', 'SMD', 'diesm@gmail.com', '123456'),
('Moises', 'Silva', 'MSM', 'moi@gmail.com', '123456'),
('German', 'Silva', 'gerzuu', 'ger@gmail.com', '123456');

insert into tags ("nameTag") values ('Noticias'), ('Terror'), ('Suspenso'), ('Superacion'), ('Comedia'), ('Gaming');

insert into posts ("title",	"description",	"authorId", "tagId")
values ('Morir ahogado', 'El barco se mecía por las holas como un juguete que es sumergido por un niño, la noche había caído sobre sus cabezas.', 2, 2),
('Los videojuegos', 'La industria del videojuego tuvo su debut comercial a comienzos de la década de 1970, cuando los costos de fabricación de los aparatos electrónicos eran mucho más manejables.', 1, 6);

insert into "comments" ( "comment", "postId") values ('Fan de los videojuegos, me encanto', 2),
('Los videojuegos dañan la cabeza', 2), ('Bastante buena la historia', 1), ('Deberias de escribir sobre dios', 2);

insert into "usersComments" ("userId", "commentsId") values (2, 1), (1, 1), (1, 3), (3, 4);
```


