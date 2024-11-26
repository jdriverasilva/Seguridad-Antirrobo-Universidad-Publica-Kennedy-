### Consultas MySQL 

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
  <img src="./images/foto1.png" width=90%>
</div>
