<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cuentas por Pagar</title>

<style>
body{
    font-family: Arial, sans-serif;
    margin:20px;
    background:#f4f4f4;
}
h1{
    color:#1f4e78;
}
table{
    width:100%;
    border-collapse:collapse;
    background:white;
}
th,td{
    border:1px solid #ddd;
    padding:8px;
}
th{
    background:#1f4e78;
    color:white;
}
button{
    padding:8px 12px;
    background:#1f4e78;
    color:white;
    border:none;
    cursor:pointer;
}
</style>

</head>
<body>

<h1>💰 Sistema de Cuentas por Pagar</h1>

<input type="text" id="proveedor" placeholder="Proveedor">
<input type="number" id="importe" placeholder="Importe">
<button onclick="agregar()">Agregar</button>

<br><br>

<table>
    <thead>
        <tr>
            <th>Proveedor</th>
            <th>Importe</th>
        </tr>
    </thead>
    <tbody id="tabla"></tbody>
</table>

<script>

let datos = JSON.parse(localStorage.getItem("cuentas")) || [];

function guardar(){
    localStorage.setItem("cuentas", JSON.stringify(datos));
}

function mostrar(){

    let tabla = document.getElementById("tabla");
    tabla.innerHTML = "";

    datos.forEach(item => {

        tabla.innerHTML += `
        <tr>
            <td>${item.proveedor}</td>
            <td>$${item.importe}</td>
        </tr>`;
    });

}

function agregar(){

    let proveedor = document.getElementById("proveedor").value;
    let importe = document.getElementById("importe").value;

    datos.push({
        proveedor,
        importe
    });

    guardar();
    mostrar
  
