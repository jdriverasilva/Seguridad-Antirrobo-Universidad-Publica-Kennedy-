## Consultas MySQL 

### 1. Cantidad de usuarios por género y localidad.

**Álgebra Relacional:** 

$$πGenero,Localidad,COUNT(∗)→Cantidad_Usuarios(σu.id_genero=g.id_genero∧u.id_residencia=r.id_residencia∧r.id_localidad=l.id_localidad(Usuarios×Genero×Residencia×Localidad))$$

**SQL equivalente:**
```sql
SELECT g.Genero, l.Localidad, COUNT(*) AS Cantidad_Usuarios
FROM usuarios u
JOIN genero g ON u.id_genero = g.id_genero
JOIN residencia r ON u.id_residencia = r.id_residencia
JOIN localidad l ON r.id_localidad = l.id_localidad
GROUP BY g.Genero, l.Localidad;

```

<div align="center">
  <img src="./images/consulta1.jpg" width=90%>
</div>

### 2. Usuarios con dispositivos de una marca específica.

**Álgebra Relacional:** 

$$πu.Nombre,u.Apellido,m.Marca,c.Referencia(σ .Marca="Samsung(Usuarios⋈Celular⋈Marca))$$

**SQL equivalente:**
```sql
SELECT u.Nombre, u.Apellido, m.Marca, c.Referencia
FROM usuarios u
LEFT JOIN celular c ON u.Imei = c.Imei
LEFT JOIN marca m ON c.Id_marca = m.Id_marca
WHERE m.Marca = "Samsung";

```
<div align="center">
  <img src="./images/consulta2.jpg" width=90%>
</div>

### 3. Cantidad de usuarios registrados en cada CAI.

**Álgebra Relacional:** 

$$π CAI,COUNT(∗)→Cantidad_Usuarios(σu.id_residencia=r.id_residencia∧r.id_localidad=cai.id_localidad(Usuarios×Residencia×CAI))$$

**SQL equivalente:**
```sql
SELECT cai.Nombre AS CAI, COUNT(*) AS Cantidad_Usuarios
FROM usuarios u
JOIN residencia r ON u.id_residencia = r.id_residencia
JOIN cai ON r.id_localidad = cai.id_localidad
GROUP BY cai.Nombre;

```
<div align="center">
  <img src="./images/consulta3.jpg" width=90%>
</div>

### 4. Usuarios registrados en un rango de edades específico.

**Álgebra Relacional:** 

$$π u.Nombre,u.Apellido,u.Fecha_de_nacimiento(σEdadEntre(18,30(Usuarios)$$

**SQL equivalente:**
```sql
SELECT u.Nombre, u.Apellido, u.Fecha_de_nacimiento
FROM usuarios u
WHERE YEAR(CURDATE()) - YEAR(STR_TO_DATE(u.Fecha_de_nacimiento, '%d-%m-%Y')) BETWEEN 18 AND 30;
SELECT u.Nombre, u.Apellido, u.nacimiento
FROM usuarios u
WHERE YEAR(CURDATE()) - YEAR(STR_TO_DATE(u.nacimiento, '%d/%m/%Y')) BETWEEN 18 AND 30;

```
<div align="center">
  <img src="./images/consulta4.jpg" width=90%>
</div>

### 5. Total de Usuarios por Estado Civil y Género.

**Álgebra Relacional:** 

$$O=τ Total_UsuariosDESC(γ Estado_civil,Genero;COUNT(∗)((usuarios⋈u.id_civil=c.id_civilcivil)⋈ u.id_genero=g.id_genero genero))$$

**SQL equivalente:**
```sql
SELECT 
    c.Estado_civil, 
    g.Genero, 
    COUNT(*) AS Total_Usuarios
FROM usuarios u
JOIN civil c ON u.id_civil = c.id_civil
JOIN genero g ON u.id_genero = g.id_genero
GROUP BY c.Estado_civil, g.Genero
ORDER BY Total_Usuarios DESC;

```
<div align="center">
  <img src="./images/consulta5.jpg" width=90%>
</div>

### 6. Usuarios con más de un registro en la tabla aplicaciones

**Álgebra Relacional:** 
π u.Nombre,u.Apellido,COUNT(a.id_app)→Total_Apps(σ u.Identificacion=a.Identificacion(Usuarios×Aplicaciones))

**SQL equivalente:**
```sql
SELECT u.Nombre, u.Apellido, COUNT(a.id_app) AS Total_Apps
FROM usuarios u
JOIN aplicacion a ON u.Identificacion = a.Identificacion
GROUP BY u.Identificacion
HAVING COUNT(a.id_app) > 1;

```
<div align="center">
  <img src="./images/imag6.jpg" width=90%>
</div>

### 7. Top 5 de localidades con mayor cantidad de usuarios

**Álgebra Relacional:** 

π Localidad,COUNT(∗)→Cantidad_Usuarios(σ u.id_residencia=r.id_residencia&r.id_localidad=l.id_localidad(Usuarios×Residencia×Localidad))

**SQL equivalente:**
```sql
SELECT l.Localidad, COUNT(*) AS Cantidad_Usuarios
FROM usuarios u
JOIN residencia r ON u.id_residencia = r.id_residencia
JOIN localidad l ON r.id_localidad = l.id_localidad
GROUP BY l.Localidad
ORDER BY Cantidad_Usuarios DESC
LIMIT 5;

```
<div align="center">
  <img src="./images/imag7.jpg" width=90%>
</div>

### 8. CAIs con el mayor número de aplicaciones asociadas

**Álgebra Relacional:** 

π CAI,COUNT(app_cai.id_app)→Total_Apps(σ cai.id_CAI=app_cai.id_CAI(CAI×App_CAI))

**SQL equivalente:**
```sql
SELECT cai.Nombre AS CAI, COUNT(app_cai.id_app) AS Total_Apps
FROM cai
JOIN app_cai ON cai.id_CAI = app_cai.id_CAI
GROUP BY cai.Nombre
ORDER BY Total_Apps DESC;

```
<div align="center">
  <img src="./images/imag8.jpg" width=90%>
</div>

### 9. Usuarios que residen en una localidad específica con sus CAIs asignados

**Álgebra Relacional:** 

π u.Nombre,u.Apellido,l.Localidad,cai.Nombre(σ l.Localidad=′Usaqueˊn′(Usuarios×Residencia×Localidad×CAI))

**SQL equivalente:**
```sql
SELECT u.Nombre, u.Apellido, l.Localidad, cai.Nombre AS CAI
FROM usuarios u
JOIN residencia r ON u.id_residencia = r.id_residencia
JOIN localidad l ON r.id_localidad = l.id_localidad
JOIN cai ON l.id_localidad = cai.id_localidad
WHERE l.Localidad = 'Usaquén';

```
<div align="center">
  <img src="./images/imag9.jpg" width=90%>
</div>

### 10. Usuarios asignados a un capitán específico

**Álgebra Relacional:** 

π u.Nombre,u.Apellido,cap.Nombre(σ cap.Nombre= ′JuanPerez ′(Usuarios×Residencia×CAI×Capitaˊn))

**SQL equivalente:**
```sql
SELECT u.Nombre, u.Apellido, cap.Nombre AS Capitan
FROM usuarios u
JOIN residencia r ON u.id_residencia = r.id_residencia
JOIN cai ON r.id_localidad = cai.id_localidad
JOIN capitan cap ON cai.id_capitan = cap.id_capitan
WHERE cap.Nombre LIKE '%Maria%';

```
<div align="center">
  <img src="./images/imag10.jpg" width=90%>
</div>
