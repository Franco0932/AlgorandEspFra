## 1. Crear cuentas en Algorand y añadirles fondos

### Conceptos Básicos

Para enviar transacciones en la cadena de bloques de Algorand, es necesario crear una cuenta.
Las cuentas básicas en Algorand están definidas por una *dirección* (o llave pública) y una *llave privada*.

La dirección es completamente pública y es la información que se da a quién nos quiera enviar Algos u otros activos/tokens. Otra forma de llamar a esta llave es "cartera" o "wallet."

La *llave privada* se utiliza para autorizar las transacciones desde tu cuenta, ya que estás deben firmase con dicha llave.
Esta llave suele estar representada por un mnemónico de 25 palabras que debe mantenerse en secreto ya que quien tenga acceso a esta llave será el dueño de los activos en ella.

### 1.1 - Crear cuentas en Algorand 

Ahora crearemos cuentas Algorand usando Python SDK. 

Para esto ejecturemos el código que se presenta a continuación las veces que requeriramos. Si lo ejecutamos una vez se imprimen en pantalla la llave privada (mnemónico de 25 palabras) y la pública (dirección), el par de llaves necesarias para interacutar con Algorand. Es importante recordar que ambas llaves deben guardarse de manera separada y segura.

```py
import algosdk

# Generate a fresh private key and associated account address
private_key, account_address = algosdk.account.generate_account()

# Convert the private key into a mnemonic which is easier to use
mnemonic = algosdk.mnemonic.from_private_key(private_key)

print("Private key mnemonic: " + mnemonic)
print("Account address: " + account_address)
```

Al ejecutar este código se mostrará el mnemónico de la llave privada y la dirección de la cuenta, por ejemplo:

```plain
Private key mnemonic: six citizen candy robot jacket regular install tell end oven piece problem venture sleep arrow decorate chalk casual patient flat start upset tent abandon bounce
Account address: ZBXIRU3KVUTZMFC2MNDHFZ5RZMEH6FYGYZ32B6BEJHQNKWTUJUBB72WL4Y
```

> **Importante** 
>
> Nunca utilices esta llave privada para mantener Algos reales (es decir, dentro de la MainNet). Únicamente úsalo para Algos "falsos" en la TestNet.

Estas cuentas ya están creadas y listas para ser utilizadas en la TestNet.

### 1.2 - Añadirles fondos a las cuentas

Ahora añadiremos 10 Algos a cada una de las cuentas. El Algo es la criptomoneda nativa de la blockchain de Algorand.

Para poder utilizar tus cuentas, necesitas añadir Algos a ellas. En la MainNet, tendrías que comprarlos en un exchange.
Sin embargo, en TestNet, puedes utilizar el [dispensador](https://bank.testnet.algorand.network/) que nos regala Algos para realizar nuestras pruebas.

Para cada cuenta, copia la dirección en el campo de texto, haz clic y llena el CAPTCHA. Da clic en "Dispense". 

Recuerda actualizar la página entre cada carga.

![](https://github.com/raldecop/AlgorandEsp/blob/main/Imagenes/AlgorandDispenser2.png)

### 1.3  - Verificar el balance de nuestras cuentas

Para comprobar el saldo de una cuenta podemos usar un explorador de blockchains. En nuestro caso usaremos [AlgoExplorer](https://testnet.explorer.perawallet.app/).

Simplemente coloca tu dirección en el buscador y podrás ver el saldo. Los exploradores de bloques te permiten observar el estado actual de las cadenas de bloques, en esta caso cada cuenta creada debería tener 10 Algos. Si no es así, vuelva al paso 1.1.

![](https://github.com/raldecop/AlgorandEsp/blob/main/Imagenes/SaldoExplorer.png)

Ten en cuenta que cada transacción de carga tarda menos de 5 segundos en ser registrada en la cadena de bloques para posteriormente ver el saldo actualizo. Y lo que es más importante, una vez que la transacción aparece en el explorador (es decir, se registra en un bloque), la transacción es definitiva y no puede revertirse ni cancelarse. Esta es una propiedad distintiva de la cadena de bloques Algorand: **finalización inmediata**.
