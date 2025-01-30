# SXE_12

### 1 

```
CREATE table EmpresasFCT (idEmpresa serial PRIMARY KEY , nombre varchar(40) , quiereAlumnos boolean, numAlumnos integer, fechaContacto date);
```
![](https://github.com/VictorQuinoa/SXE_12/blob/main/1_12.png?raw=true)

### 2 

```
INSERT into EmpresasFCT (nombre, quierealumnos, numalumnos, fechacontacto) values ('Abanicos S.A' , 'true', '7', '2024/11/12' ); 
```

![](https://github.com/VictorQuinoa/SXE_12/blob/main/2.png?raw=true)

### 3 

```
Select * from empresasfct order by fechacontacto desc;
```

![](https://github.com/VictorQuinoa/SXE_12/blob/main/3_12.png?raw=true)
