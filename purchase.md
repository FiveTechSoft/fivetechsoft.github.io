---
layout: default
---

<script>
var precio_producto = new Array( 0, 570, 380, 350, 230, 350, 230, 260, 560, 350, 230, 280, 280 );
var nombre_producto = new Array( 'Pick one',
                                 'FTDN',
                                 'FTDN renewal',
                                 'FWH for Harbour/xHarbour 32',
                                 'Upgrade an old version to current FWH 32',
                                 'FWH for Harbour 64',
                                 'Upgrade an old version to current FWH 64',
                                 'FiveTouch',
                                 'FiveTouch Developer Edition',
                                 'FWPPC for Pocket PC',
                                 'Upgrade an old version to current FWPPC',
                                 'FiveMac for Mac OSX',
                                 'FiveLinux' );

function PrecioTotal()
{
	 document.form1.total.value = precio_producto[ document.form1.lista_productos.value ];
	
   if( document.form1.por_email.value == -60 )
   {
      document.form1.total.value -= 60;
   }
   else
   {
      if( document.form1.portes.value != '-' ) // tiene portes
	    {
	       document.form1.total.value = parseInt( document.form1.total.value ) + 
	                                    parseInt( document.form1.portes.value );
	    }  
   }
}

function validar( form )
{
	 if( form.lista_productos.value == "0" )
	 {
	    alert( "Please select a product" );
	    form.lista_productos.focus();
	    return false;	
	 }
	
 	 if( ( form.portes.value == '-' ) && ( form.por_email.value == 0 ) )
	 {
	    alert( "Please select a shipping area" );
	    form.portes.focus();
	    return false;
	 }

   if( form.remitente.value == "" )
	 {
	    alert( "Please enter your email" );
	    form.remitente.focus();
	    return false;
	 }

   if( form.company.value == "" )
	 {
	    alert( "Please, enter the company name" );
	    form.company.focus();
	    return false;
	 }

   if( form.credit_card.value == "" )
   {
	    alert( "Please, select your credit card" );
	    form.credit_card.focus();
	    return false;
	 }

   if( form.vattax.value == "" )
   {
	    alert( "Please, enter your vat/tax number or zero if it does not apply" );
	    form.vattax.focus();
      return false;
	 }

   if( form.credit_owner.value == "" )
   {
	    alert( "Please, enter the name of the card owner" );
	    form.credit_owner.focus();
	    return false;
	 }

   if( form.credit_number.value == "" )
   {
	    alert( "Please, enter your credit card number" );
	    form.credit_number.focus();
	    return false;
	 }

   if( form.security_code.value == "" )
   {
	    alert( "Please, enter your credit card security code" );
	    form.security_code.focus();
	    return false;
	 }

   if( form.expdate.value == "" )
   {
	    alert( "Please, enter the expiration date" );
	    form.expdate.focus();
	    return false;
	 }

	 // Almcenamos el precio del producto
	 form.producto.value = precio_producto[ form.lista_productos.value ];

	 //Almcenamos el nombre del producto
	 form.product.value = nombre_producto[ form.lista_productos.value ];

	//selecionamos el area viendo su precio
	switch( form.portes.value )
	{
	   case "-":
	      form.shipping_area.value = "-";
	      break;

	   case "20":
	      form.shipping_area.value = "Spain & Portugal";
	      break;

     case "52":
	      form.shipping_area.value = "UK, Benelux, Germany, France & Italy";
	      break;

     case "58":
	      form.shipping_area.value = "Austria, Denmark, Finland, Sweden, Greece & Irland";
	      break;

     case "85":
	      form.shipping_area.value = "Rest of Europe";
	      break;

     case "87":
	      form.shipping_area.value = "USA, Canada & Puerto Rico";
	      break;

     case "96":
	      form.shipping_area.value = "Central & South America";
	      break;

     case "110":
	      form.shipping_area.value = "Rest of the World";
	      break;
	}

	// vemos si el envio es por email
	if( form.por_email.value == 0 )
	{
	   form.viamail.value = "No";
	}
	else
	{
	   form.viamail.value = "Yes";
	}

	form.submit();
}
</script>

<div style="clear: left;"></div>
<blockquote>
	<br>
	<h1>Buy your FIVETECH Product Today!</h1><br>
	<p>Please fill the following form:</p>
    <form action="confirm.php" method="POST" name="form1">
        <input type="hidden" name="product" value><input
        type="hidden" name="producto" value><input type="hidden"
        name="viamail" value><input type="hidden"
        name="shipping_area" value><table border="0">
            <tr>
                <td width="256" height="34"><font size="2"
                face="Verdana">Please select a product</font></td>
                <td width="367"><font size="2" face="Verdana"><!--aki se almacena nombre del producto--> <!--aki se almacena precio del producto--> <!--si se modifican los 
valores hay que actualizar los arrays precio_producto y nombre producto de la linea 38 y 39--> 
                <select name="lista_productos" size="1"
                id="lista_productos" onchange="PrecioTotal()">
                    <option selected value="0">Select one</option>
                    <option value="1">FTDN</option>
                    <option value="2">FTDN Renewal</option>
                    <option value="3">FWH for Harbour/xHarbour 32</option>
                    <option value="4">Upgrade an old version to current FWH 32</option>
                    <option value="5">FWH for Harbour 64</option>
                    <option value="6">Upgrade an old version to current FWH 64</option>
                    <option value="7">FiveTouch</option>
                    <option value="8">FiveTouch Developer Edition</option>
                    <option value="9">FiveWin for Pocket PC (FWPPC)</option>
                    <option value="10">Upgrade an old version to current FWPPC</option>
                    <option value="11">FiveMac for Mac OSX</option>
                    <option value="12">FiveLinux</option>
                </select> </font></td>
            </tr>

            <tr>
                <td height="33"><font size="2"
                face="Verdana, Arial, Helvetica, sans-serif">Email delivery (60 Euros disccount)</font></td>
                <td><!--aki se almacena si el envio es por email en formato texto--> <select name="por_email" size="1"
                onchange="PrecioTotal()">
                    <option selected value="-60">Yes</option>
                    <option value="0">No</option>
                </select></td>
            </tr>
            <tr>
                <td height="42"><font size="2" face="Verdana">Shipping expenses</font></td>
                <td><font face="Verdana"><!--<aki se almacena el area selecionada--> <!--si se cambian los precios hay q cambiar los valores del switch de la linea 122--> 
<select name="portes"
                size="1" onchange="PrecioTotal()">
                    <option selected value="-">Not applicable</option>
                    <option value="20">20 euros - España & Portugal</option>
                    <option value="52">52 euros - UK, Benelux, Germany, France & Italy</option>
                    <option value="58">58 euros - Austria, Denmark, Finland, Sweden, Greece & Ireland</option>
                    <option value="85">85 euros - Rest of Europe</option>
                    <option value="87">87 euros - USA, Canada & Puerto Rico</option>
                    <option value="96">96 euros - Central & south America</option>
                    <option value="110">110 euros - Rest of the world</option>
                </select> </font></td>
            </tr>
            <tr>
                <td><font size="2" face="Verdana">Price</font></td>
                <td><input type="text" size="5" name="total"
                value="0" class="caja" readonly="true"> <font
                size="2"
                face="Verdana, Arial, Helvetica, sans-serif">Euros</font><font
                face="Verdana">&nbsp; </font></td>
            </tr>
            <tr>
            </tr>
            <tr>
                <td><font size="2" face="Verdana">Email address</td>
                <td><input type="text" size="35" name="remitente"></td>
            </tr>
            <tr>
                <td><font size="2" face="Verdana">Company name</font></td>
                <td><input type="text" size="35" name="company"></td>
            </tr>
            <tr>
                <td><font size="2" face="Verdana">Address</font></td>
                <td><input type="text" size="45" name="address1"
                id="address1"></td>
            </tr>
            <tr>
                <td><font size="2" face="Verdana">Address</font></td>
                <td><input type="text" size="45" name="address2"
                id="address2"></td>
            </tr>
            <tr>
                <td><font size="2" face="Verdana">City</font></td>
                <td><input type="text" size="35" name="city"
                id="city"></td>
            </tr>
            <tr>
                <td><font size="2" face="Verdana">State</font></td>
                <td><input type="text" size="35" name="state"
                id="state"></td>
            </tr>
            <tr>
                <td><font size="2" face="Verdana">ZIP code</font></td>
                <td><input type="text" size="11"
                name="Postal_code" id="Postal_code"></td>
            </tr>
            <tr>
                <td><font size="2" face="Verdana">Country</font></td>
                <td><input type="text" size="20" name="Country"
                id="Country"></td>
            </tr>
            <tr>
                <td><font size="2" face="Verdana">VAT (if applicable)</font></td>
                <td><input type="text" size="20" name="vattax"
                id="vattax"></td>
            </tr>
            <tr>
                <td><font size="2" face="Verdana">Phone</font></td>
                <td><input type="text" size="20" name="phone"
                id="phone"></td>
            </tr>
            <tr>
                <td><font size="2" face="Verdana">Credit card</font></td>
                <td><font face="Verdana"><select
                name="credit_card" size="1" id="credit_card">
                    <option selected>Select one</option>
                    <option value="VisaCard">VisaCard</option>
                    <option value="MasterCard">MasterCard</option>
                    <option value="AmericanExpress">American Express</option>
                    <option value="EuroCard">EuroCard</option>
                </select> </font></td>
            </tr>
            <tr>
                <td><font size="2" face="Verdana">Name on card</font></td>
                <td><input type="text" size="35"
                name="credit_owner" id="credit_owner"></td>
            </tr>
            <tr>
                <td><font size="2" face="Verdana">Card number</font></td>
                <td><input type="text" size="35"
                name="credit_number" id="credit_number"></td>
            </tr>
            <tr>
                <td><font size="2" face="Verdana">Security code</font></td>
                <td><input type="text" size="10" name="security_code"
                id="security_code">
                <a href="http://en.wikipedia.org/wiki/Card_Security_Code">
                <font size="2" face="Verdana">
                What is this ?</font></a></td>
            </tr>
            <tr>
                <td><font size="2" face="Verdana">Expiration date</font></td>
                <td><input type="text" size="10" name="expdate"></td>
            </tr>
        </table>
        <p><br><input type="button"
        value="Submit Order" onclick="validar(form1)" class="btn"></p>
    </form>
    <p><font size="2" face="Verdana">If you don't want to order on Internet, print this order and
    mail it to the following address. Please sign it.<br>
    </font></p>
    <table border="0">
        <tr>
            <td><font size="3"><strong>FIVETECH SOFTWARE S.L</strong></font></td>
        </tr>
        <tr>
            <td><font size="2" face="Verdana">Urb. El Rosario</font></td>
        </tr>
        <tr>
            <td><font size="2" face="Verdana">Avda. del Rosario
            34-A</font></td>
        </tr>
        <tr>
            <td><font size="2" face="Verdana">29600 Marbella -
            SPAIN</font></td>
        </tr>
        <tr></tr>
        <tr>
            <td>email: <a href="mailto:alinares@fivetechsoft.com">alinares@fivetechsoft.com</td>
        </tr>
    </table>
</blockquote>
