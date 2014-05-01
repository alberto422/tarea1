tarea1
======
<!DOCTYPE html>
<!--
To change this license header, choose License Headers in Project Properties.
To change this template file, choose Tools | Templates
and open the template in the editor.

        PROGRAMACIÓN APLICADA A LA WEB
        ARIAS MERO ALBERTO FERNANDO
        TERCER NIVEL "A"

-->
<html>
    <head>
        <title>Arias Mero Alberto Fernando</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width">
    </head>
    <body bgcolor="696969" onload="datos()">
        <div align="center"><marquee><h1><font color="red">Programación Aplicada a la Web</font></h1></marquee></div><br><br>
      
        <!--NUMEROS PRIMOS-->
        <h3><font color="red">Primer Ejercicio</font></h3>
        
       Números Primos : <input id="valor" name="valor" type="text"  />
        <input  name="Validar" onclick="ValidarPrimos()" value="Validar"  type="button" id="btnvalidar"/><br><br>
  
         <!--NUMEROS HEXADECIMALES-->
        Números Hexadecimales : <input type="text" id="hexadecimalIngresado"/>
        <input type="button" id="Validar" value="Validar" onclick="validarHexadecimal()"/><br><br>
        
        <!--NUMERO DE CEDULA-->
        Numero de Cédula :<input type="text" id="entrada"  />
        <input type="button" id="validar" value="Validar" onclick="validarCedula()"/><br><br><br><br>
        
        
        <h3><font color="red">Segundo Ejercicio</font></h3>
         <h5>Números Binarios</h5>
        <!--NUMEROS BINARIOS-->
       Ingrese un número Binario :<input type="text" id="binarioUno"/><br><br>
       Ingrese segundo número Binario :<input type="text" id="binarioDos"/><br><br>
        <input type="button" id="Sumar" value="Sumar" onclick="Binarios(document.getElementById('binarioUno').value, document.getElementById('binarioDos').value)"/><br><br><br><br>
        
         <!--NUMEROS INVERTIDO-->
         <h5>Invertir Oraciones o Palabras</h5>
        Oracion :<input type="text" id="frase"/><br><br>
        Invertir :<input type="text" id="palabra"/><br><br>
        <input type="button" id="invertir" value="Aceptar" onclick="sumaDeBinarios(document.getElementById('frase').value, document.getElementById('palabra').value)"/><br><br><br><br>
        <br>
     
        
         <!--FACTURA-->
         <h3><font color="red">Tercer  Ejercicio</font></h3><br>
         <h4><font color="red">FACTURA</font></h4>
         Cliente: <select id="listaClientes"></select><br>
        <hr>
        Producto:  <select id="listaProducto"></select>
        Precio Unitario: <input type="text" id="precioUnit" />
        Cantidad: <input type="text" id="cantidad" onchange="total()"/>

        Total: <input type="text" id="total"/><br><br>
        <input type="button" id="agregar" value="Ingresar Factura" onclick="crearFilaProductoIngresado()"/><br>
        <hr><hr>

        Compras Recibidas: <br>
        Producto - Precio - Cantidad - Total
        <div id="contenido">

        </div>
        <hr>
        Subtotal : <input type="text" id="subtotal" value="0"/><br><br>
        IVA : <input type="text" id="iva"/><br><br>
        Descuento : <input type="text" id="descuento"/><br><br>
        Total : <input type="text" id="totalFinal"/><br><br>
        
    </body>
</html>
<script>
    //FUNCIÓN PARA VALIDAR LOS NUMEROS PRIMOS
    function ValidarPrimos() {
                var dato = document.getElementById("valor").value;
                var divisoresEncontrados = 0;
                for (i = 0; i <= dato; i++) {
                    var residuo = dato % i;
                    if (residuo == 0) {
                        divisoresEncontrados++;
                    }
                }
                if (divisoresEncontrados == 2 || dato == 1) {
                    
                   alert("Es un Número Primo")
                } else {
                  document.getElementById("valor").value= "";
                 alert("No es un Número Primo")
                }
            }
            
            //FUNCIÓN PARA VALIDAR LOS NUMEROS HEXADECIMALES
             function validarHexadecimal() {
                var dato = document.getElementById('hexadecimalIngresado').value;
                var letras = dato.split("");
                for (i = 0; i < letras.length; i++) {
                    if ((letras[i] != 1) && (letras[i] != 2)&&(letras[i] != 3) && (letras[i] != 4)&&(letras[i] != 5)&&
                        (letras[i] != 6) && (letras[i] != 7)&&(letras[i] != 8) && (letras[i] != 9)&&(letras[i] != "A")&&    
                        (letras[i] != "B") && (letras[i] != "C")&&(letras[i] != "D") && (letras[i] != "Ë")&&(letras[i] != "F")  
                    ) {
                        alert('Error');
                    }
                }
            }
            
             //FUNCIÓN PARA VALIDAR NUMERO DE CEDULA
            function validarCedula()
            {
                var cedula = document.getElementById("entrada").value;
                array = cedula.split("");
                valor = array.length;
                if (valor == 10)
                {
                    respues = 0;
                    valor1 = (array[9] * 1);
                    for (i = 0; i < (valor - 1); i++)
                    {
                        max = 0;
                        if ((i % 2) != 0) {
                            respues = respues + (array[i] * 1);
                        }
                        else
                        {
                            max = array[i] * 2;
                            if (max > 9)
                                respues = respues + (max - 9);
                            else
                                respues = respues + max;
                        }
                    }
                    unite = respues / 10;
                    unite = Math.floor(unite);
                    unite = (unite + 1) * 10;
                    finix = (unite - respues);
                    if ((finix == 10 && valor1 == 0) || (finix == valor1)) {
                        alert("Número de Cedula Correcta");
                        return true;
                    }
                    else
                    {
                        alert("Número de Cedula Incorrecta");
                        return false;
                    }
                }
                else
                {
                    alert("Error. \n\nIngrese la Cédula nuevamente");
                    return false;
                }
            }
            
            
           
        </script>
        
        
        <script>
             //FUNCIÓN DE NUMEROS BINARIOS
            function Binarios(primer, segundo) {
                var num1 = parseInt(primer, 2);
                var num2 = parseInt(segundo, 2);
                var sumaDecimal = num1 + num2;
                var sumaBinario = deciToBin(sumaDecimal);
                alert('Decimal: ' + sumaDecimal + 'Binario: ' + sumaBinario);
            }

            function deciToBin(arg)
            {
                res1 = 999;
                args = arg;
                while (args > 1)
                {
                    arg1 = parseInt(args / 2);
                    arg2 = args % 2;
                    args = arg1;
                    if (res1 == 999)
                    {
                        res1 = arg2.toString();
                    }
                    else
                    {
                        res1 = arg2.toString() + res1.toString();
                    }
                }
                if (args == 1 && res1 != 999)
                {
                    res1 = args.toString() + res1.toString();
                }
                else if (args == 0 && res1 == 999)
                {
                    res1 = 0;
                }
                else if (res1 == 999)
                {
                    res1 = 1;
                }
                var ll = res1.length;
                while (ll % 4 != 0)
                {
                    res1 = "0" + res1;
                    ll = res1.length;
                }
                return res1;
            }
            
            
             //FUNCIÓN DE NUMERO INVERTIDO
            function sumaDeBinarios(fraseRecivida, palabraRecivida) {
                var palabras = fraseRecivida.split(" ");
                for (i = 0; i < palabras.length; i++) {
                    if (palabras[i] == palabraRecivida) {
                        alert(invertir(palabras[i]));
                    }
                }
            }
            function invertir(cadena) {
                var x = cadena.length;
                var cadenaInvertida = "";
                while (x >= 0) {
                    cadenaInvertida = cadenaInvertida + cadena.charAt(x);
                    x--;
                }
                return cadenaInvertida;
            }

        </script>
        
        
        
        <script>
            
                 //FUNCION DE FACTURA
            function datos() {
                var clientes = ["Alberto", "Maria", "Ana", "Jorge"];
                var productos = ["Zapatos", "Camisa", "Pantalon", "Medias"];
                var listaClientesDatos = document.getElementById('listaClientes');
                for (var i = 0; i < clientes.length; i++) {
                    var opt = document.createElement('option');
                    opt.innerHTML = clientes[i];
                    opt.value = clientes[i];
                    listaClientesDatos.appendChild(opt);
                }
                var listaProductosDatos = document.getElementById('listaProducto');
                for (var i = 0; i < productos.length; i++) {
                    var opt = document.createElement('option');
                    opt.innerHTML = productos[i];
                    opt.value = productos[i];
                    listaProductosDatos.appendChild(opt);
                }

            }
            function total() {
                var unitario = document.getElementById('precioUnit').value;
                var cantidad = document.getElementById('cantidad').value;
                var total = parseFloat(unitario) * parseFloat(cantidad);
                document.getElementById('total').value = total;
            }
            function crearFilaProductoIngresado() {
                var subtotal = document.getElementById('subtotal').value;
                document.getElementById('subtotal').value = parseFloat(subtotal) + parseFloat(document.getElementById('total').value);
                var subtotalNuevo = document.getElementById('subtotal').value;
                document.getElementById('iva').value = parseFloat(subtotalNuevo) * 0.12;
                var ivaNuevo = document.getElementById('iva').value;
                document.getElementById('descuento').value = (parseFloat(subtotalNuevo) + parseFloat(ivaNuevo)) * 0.05;
                var descuentoNuevo = document.getElementById('descuento').value;
                document.getElementById('totalFinal').value = (parseFloat(subtotalNuevo) + parseFloat(ivaNuevo)) - parseFloat(descuentoNuevo);
                capotTexto = document.createElement('input');
                capotTexto.type = "text";
                capotTexto.name = "producto";
                capotTexto.id = "produc";
                capotTexto.value = document.getElementById('listaProducto').value + '     -     ' + document.getElementById('precioUnit').value + '     -     ' + document.getElementById('cantidad').value + '     -     ' + document.getElementById('total').value;
                capotTexto.size = "50";
                document.getElementById('contenido').appendChild(capotTexto);
                salto = document.createElement('br');
                document.getElementById('contenido').appendChild(salto);
            }

        </script>
