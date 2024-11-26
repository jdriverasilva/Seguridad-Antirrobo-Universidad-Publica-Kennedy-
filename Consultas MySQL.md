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








