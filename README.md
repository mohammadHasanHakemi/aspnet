

cmd{
run project:
dotnet watch run

create migration & database:
dotnet ef database drop
dotnet ef migrations remove
dotnet ef migrations add InitialCreate
dotnet ef database update
}


sql query{


frogen key:
-- تغییر charset و collation دیتابیس به utf8mb4_persian_ci
ALTER DATABASE `rmw_asp` CHARACTER SET = utf8mb4 COLLATE = utf8mb4_persian_ci;

-- تغییر charset و collation برای جداول به utf8mb4_persian_ci و موتور به InnoDB
ALTER TABLE `Albums` CONVERT TO CHARACTER SET utf8mb4 COLLATE utf8mb4_persian_ci, ENGINE = InnoDB;
ALTER TABLE `Musics` CONVERT TO CHARACTER SET utf8mb4 COLLATE utf8mb4_persian_ci, ENGINE = InnoDB;


-- ایجاد رابطه Foreign Key در جدول Musics برای اتصال به جدول Albums
ALTER TABLE `Musics`
ADD CONSTRAINT `FK_Musics_Albums_AlbumId`
FOREIGN KEY (`AlbumId`) REFERENCES `Albums`(`Id`)
ON DELETE NO ACTION;

-- اطمینان از این که تغییرات به درستی اعمال شده‌اند
SHOW TABLE STATUS WHERE Name IN ('Albums', 'Musics');
}
ssd
sd