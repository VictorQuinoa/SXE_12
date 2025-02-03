# SXE_12

### 1 

Crear tabla EmpresasFCT con una serie de campos.

```
CREATE table EmpresasFCT (idEmpresa serial PRIMARY KEY , nombre varchar(40) , quiereAlumnos boolean, numAlumnos integer, fechaContacto date);
```
![](https://github.com/VictorQuinoa/SXE_12/blob/main/1_12.png?raw=true)

### 2 

Inserción de 5 registros.

```
INSERT into EmpresasFCT (nombre, quierealumnos, numalumnos, fechacontacto) values ('Abanicos S.A' , 'true', '7', '2024/11/12' ); 
```

![](https://github.com/VictorQuinoa/SXE_12/blob/main/2.png?raw=true)

### 3 

Datos de EmpresasFCT ordenadas por fecha de contacto.

```
Select * from empresasfct order by fechacontacto desc;
```

![](https://github.com/VictorQuinoa/SXE_12/blob/main/3_12.png?raw=true)

### 4

Realiza una consulta que permita obtener un listado de todos los contactos de
Odoo (no empresas) con la siguiente información:

- Nombre.
- Cuya ciudad sea Tracy.
- Nombre comercial de la empresa
  
Ordenados alfabéticamente por el nombre comercial de la empresa,

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

Obtén un listado de empresas proveedoras, que han emitido algún reembolso.

```
SELECT invoice_partner_display_name, name ,
invoice_date_due, amount_untaxed 
FROM account_move WHERE move_type= 'in_refund'
ORDER BY invoice_date DESC;
```

![](https://github.com/VictorQuinoa/SXE_12/blob/main/5.png?raw=true)

### 6 
Obtén un listado de empresas clientes, a las que se les ha emitido más de dos facturas de venta (solo venta) cofirmadas, mostrando los siguientes datos:

- Nombre de la empresa
- Número de facturas
- Total facturado SIN IMPUESTOS

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

Crea una sentencia que actualice el correo de los contactos cuyo dominio es @bilbao.example.com a @bilbao.bizkaia.neus

```
UPDATE res_partner SET  email= 
REPLACE(email, '@bilbao.example.com', '@bilbao.bizkaia.eus')   
WHERE email like '%@bilbao.example.com';
```

![](https://github.com/VictorQuinoa/SXE_12/blob/main/7.png?raw=true)

### 8

Crea una sentencia que elimine todos los contactos pertenecientes a la empresa “Ready Mat”, pero mantén la empresa.


![](https://github.com/VictorQuinoa/SXE_12/blob/main/READYMAT%20antes.png?raw=true)

```
DELETE FROM res_partner
WHERE commercial_company_name = 'Ready Mat' 
AND is_company = FALSE;
```

![](https://github.com/VictorQuinoa/SXE_12/blob/main/8.png?raw=true)
![](https://github.com/VictorQuinoa/SXE_12/blob/main/Despues.png?raw=true)
