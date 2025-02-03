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

### 4

```
SELECT name AS Nombre, city AS Ciudad, 
commercial_company_name AS Nombre_Comercial_Empresa
FROM res_partner 
WHERE is_company = FALSE 
AND city = 'Tracy'
ORDER BY commercial_company_name ASC;
```

![](https://github.com/VictorQuinoa/SXE_12/blob/main/4.png?raw=true)

### 5

```
SELECT invoice_partner_display_name, name ,
invoice_date_due, amount_untaxed 
FROM account_move WHERE move_type= 'in_refund'
ORDER BY invoice_date DESC;
```

![](https://github.com/VictorQuinoa/SXE_12/blob/main/5.png?raw=true)

### 6 

```
SELECT 
    invoice_partner_display_name ,
    COUNT(DISTINCT name),
    SUM(DISTINCT amount_untaxed) 
FROM account_move 
WHERE move_type = 'out_invoice'  
AND state = 'posted'
GROUP BY invoice_partner_display_name
HAVING COUNT(DISTINCT name) > 2;
```
![](https://github.com/VictorQuinoa/SXE_12/blob/main/6.png?raw=true)

### 7 

```
UPDATE res_partner SET  email= 
REPLACE(email, '@bilbao.example.com', '@bilbao.bizkaia.eus')   
WHERE email like '%@bilbao.example.com';
```

![](https://github.com/VictorQuinoa/SXE_12/blob/main/7.png?raw=true)

### 8

![](https://github.com/VictorQuinoa/SXE_12/blob/main/READYMAT%20antes.png?raw=true)

```
DELETE FROM res_partner
WHERE commercial_company_name = 'Ready Mat' 
AND is_company = FALSE;
```

![](https://github.com/VictorQuinoa/SXE_12/blob/main/8.png?raw=true)
![](https://github.com/VictorQuinoa/SXE_12/blob/main/Despues.png?raw=true)
