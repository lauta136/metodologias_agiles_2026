# Ejercicio Nro: 13-TDD — Resolución

## Enunciado
Tu tarea es desarrollar una aplicación informática utilizando la técnica TDD para gestionar una cuenta bancaria. La aplicación debe permitir a los usuarios abrir una cuenta, realizar depósitos, hacer retiros y transferir fondos entre cuentas. A continuación se detallan las etapas de desarrollo utilizando TDD:
### Etapa 1: Especificación y prueba inicial
1. Especifica los requisitos básicos del sistema y las funcionalidades clave, como la apertura de cuenta, depósito de fondos, retiro de fondos y transferencia de fondos.
2. Escribe una prueba inicial que verifique si el sistema puede crear una instancia de una cuenta bancaria y obtener su saldo inicial.
### Etapa 2: Desarrollo de las funcionalidades básicas
3. Implementa la funcionalidad para abrir una cuenta bancaria, asegurándote de que se cumplan los requisitos especificados. Ejecuta la prueba y verifica que pase correctamente.
4. Implementa la funcionalidad para realizar depósitos en una cuenta bancaria. Ejecuta las pruebas y verifica que pasen correctamente.
5. Implementa la funcionalidad para realizar retiros de una cuenta bancaria. Ejecuta las pruebas y verifica que pasen correctamente.
6. Implementa la funcionalidad para transferir fondos entre cuentas bancarias. Ejecuta las pruebas y verifica que pasen correctamente.
### Etapa 3: Pruebas adicionales y mejoras
7. Escribe pruebas adicionales para cubrir casos de prueba específicos, como intentar retirar más dinero del disponible en una cuenta o transferir fondos a una cuenta inexistente.
8. Ejecuta todas las pruebas y verifica que pasen correctamente.
9. Refactoriza tu código si es necesario para mejorar su estructura, legibilidad y eficiencia.
10. Ejecuta todas las pruebas nuevamente para asegurarte de que el código refactorizado no haya introducido errores.
### Etapa 4: Cobertura completa de pruebas
11. Asegúrate de que todas las funcionalidades del sistema estén cubiertas por pruebas automatizadas.
12. Examina los casos límite y situaciones excepcionales para garantizar que el sistema se comporte correctamente en todos los escenarios.
13. Ejecuta todas las pruebas y verifica que pasen correctamente.
Recuerda seguir el enfoque TDD, donde agregarás una prueba antes de implementar cada funcionalidad y verificarás que todas las pruebas pasen antes de pasar a la siguiente etapa.
Esto te ayudará a desarrollar una aplicación confiable, mantenible y que cumpla con los requisitos establecidos.

## Resolución

### Etapa 1: Especificación y prueba inicial

**Requisitos del sistema:**
- Abrir una cuenta con titular y saldo inicial (opcional, por defecto 0).
- Depositar fondos (montos positivos).
- Retirar fondos (validando saldo suficiente).
- Transferir fondos entre cuentas (validando cuenta destino y saldo suficiente).

Empezamos escribiendo la prueba más simple posible: crear una cuenta y verificar su saldo inicial.

```python
# test_cuenta_bancaria.py
def test_cuenta_nueva_tiene_saldo_cero():
    cuenta = CuentaBancaria("Rocío Fernández")
    assert cuenta.saldo == 0.0
```

Esta prueba falla porque `CuentaBancaria` todavía no existe. Recién ahora escribimos el código mínimo para que pase.

### Etapa 2: Desarrollo de las funcionalidades básicas

`cuenta_bancaria.py`

```python
class SaldoInsuficienteError(Exception):
    """Se dispara al intentar retirar/transferir más de lo disponible."""


class CuentaInexistenteError(Exception):
    """Se dispara al operar contra una cuenta destino inválida."""


class CuentaBancaria:
    def __init__(self, titular: str, saldo_inicial: float = 0.0):
        if saldo_inicial < 0:
            raise ValueError("El saldo inicial no puede ser negativo.")
        self.titular = titular
        self._saldo = saldo_inicial

    @property
    def saldo(self) -> float:
        return self._saldo

    def depositar(self, monto: float) -> None:
        if monto <= 0:
            raise ValueError("El depósito debe ser mayor a cero.")
        self._saldo += monto

    def retirar(self, monto: float) -> None:
        if monto <= 0:
            raise ValueError("El retiro debe ser mayor a cero.")
        if monto > self._saldo:
            raise SaldoInsuficienteError(
                f"Saldo disponible ${self._saldo:.2f}, se pidió retirar ${monto:.2f}."
            )
        self._saldo -= monto

    def transferir(self, destino: "CuentaBancaria", monto: float) -> None:
        if destino is None:
            raise CuentaInexistenteError("La cuenta destino no existe.")
        self.retirar(monto)
        destino.depositar(monto)

    def __repr__(self) -> str:
        return f"CuentaBancaria(titular={self.titular!r}, saldo={self._saldo:.2f})"
```

Cada método se implementó recién después de escribir su prueba correspondiente y verla fallar primero (ciclo rojo-verde).

### Etapa 3: Pruebas adicionales y mejoras

`test_cuenta_bancaria.py`

```python
import pytest
from cuenta_bancaria import CuentaBancaria, SaldoInsuficienteError, CuentaInexistenteError


# --- Apertura de cuenta ---
class TestAperturaDeCuenta:
    def test_guarda_el_nombre_del_titular(self):
        cuenta = CuentaBancaria("Rocío Fernández")
        assert cuenta.titular == "Rocío Fernández"

    def test_saldo_por_defecto_es_cero(self):
        cuenta = CuentaBancaria("Rocío Fernández")
        assert cuenta.saldo == 0.0

    def test_permite_definir_saldo_inicial(self):
        cuenta = CuentaBancaria("Rocío Fernández", saldo_inicial=750.0)
        assert cuenta.saldo == 750.0

    def test_rechaza_saldo_inicial_negativo(self):
        with pytest.raises(ValueError):
            CuentaBancaria("Rocío Fernández", saldo_inicial=-50.0)


# --- Depósitos ---
class TestDepositos:
    def setup_method(self):
        self.cuenta = CuentaBancaria("Nicolás Bravo", saldo_inicial=100.0)

    def test_suma_el_monto_al_saldo(self):
        self.cuenta.depositar(150.0)
        assert self.cuenta.saldo == 250.0

    def test_admite_depositos_sucesivos(self):
        self.cuenta.depositar(20.0)
        self.cuenta.depositar(30.0)
        assert self.cuenta.saldo == 150.0

    def test_rechaza_deposito_de_cero(self):
        with pytest.raises(ValueError):
            self.cuenta.depositar(0)

    def test_rechaza_deposito_negativo(self):
        with pytest.raises(ValueError):
            self.cuenta.depositar(-25.0)


# --- Retiros ---
class TestRetiros:
    def setup_method(self):
        self.cuenta = CuentaBancaria("Valentina Ossa", saldo_inicial=600.0)

    def test_resta_el_monto_del_saldo(self):
        self.cuenta.retirar(100.0)
        assert self.cuenta.saldo == 500.0

    def test_permite_retirar_el_saldo_completo(self):
        self.cuenta.retirar(600.0)
        assert self.cuenta.saldo == 0.0

    def test_rechaza_retiro_de_cero(self):
        with pytest.raises(ValueError):
            self.cuenta.retirar(0)

    def test_rechaza_retiro_negativo(self):
        with pytest.raises(ValueError):
            self.cuenta.retirar(-10.0)

    def test_lanza_error_si_no_hay_fondos_suficientes(self):
        with pytest.raises(SaldoInsuficienteError):
            self.cuenta.retirar(1000.0)

    def test_saldo_no_cambia_si_el_retiro_falla(self):
        with pytest.raises(SaldoInsuficienteError):
            self.cuenta.retirar(1000.0)
        assert self.cuenta.saldo == 600.0


# --- Transferencias ---
class TestTransferencias:
    def setup_method(self):
        self.origen = CuentaBancaria("Tomás Reyes", saldo_inicial=900.0)
        self.destino = CuentaBancaria("Camila Soto", saldo_inicial=300.0)

    def test_disminuye_saldo_de_origen(self):
        self.origen.transferir(self.destino, 200.0)
        assert self.origen.saldo == 700.0

    def test_aumenta_saldo_de_destino(self):
        self.origen.transferir(self.destino, 200.0)
        assert self.destino.saldo == 500.0

    def test_el_total_entre_ambas_cuentas_no_cambia(self):
        total_previo = self.origen.saldo + self.destino.saldo
        self.origen.transferir(self.destino, 350.0)
        total_actual = self.origen.saldo + self.destino.saldo
        assert total_previo == total_actual

    def test_lanza_error_si_origen_no_tiene_fondos(self):
        with pytest.raises(SaldoInsuficienteError):
            self.origen.transferir(self.destino, 5000.0)

    def test_saldos_no_cambian_si_transferencia_falla(self):
        with pytest.raises(SaldoInsuficienteError):
            self.origen.transferir(self.destino, 5000.0)
        assert self.origen.saldo == 900.0
        assert self.destino.saldo == 300.0

    def test_lanza_error_si_la_cuenta_destino_no_existe(self):
        with pytest.raises(CuentaInexistenteError):
            self.origen.transferir(None, 100.0)

    def test_saldo_de_origen_no_cambia_si_destino_es_invalido(self):
        with pytest.raises(CuentaInexistenteError):
            self.origen.transferir(None, 100.0)
        assert self.origen.saldo == 900.0
```

No hizo falta refactorizar la clase `CuentaBancaria`: el método `retirar()` ya se reutiliza dentro de `transferir()`, evitando duplicar la validación de fondos.

### Etapa 4: Cobertura completa de pruebas

```python
class TestEscenariosCombinados:
    def test_deposito_seguido_de_dos_retiros(self):
        cuenta = CuentaBancaria("Franco Ibarra", saldo_inicial=0.0)
        cuenta.depositar(800.0)
        cuenta.retirar(300.0)
        cuenta.retirar(200.0)
        assert cuenta.saldo == 300.0

    def test_cadena_de_transferencias_entre_tres_cuentas(self):
        a = CuentaBancaria("A", saldo_inicial=500.0)
        b = CuentaBancaria("B", saldo_inicial=0.0)
        c = CuentaBancaria("C", saldo_inicial=0.0)
        a.transferir(b, 200.0)
        b.transferir(c, 80.0)
        assert a.saldo == 300.0
        assert b.saldo == 120.0
        assert c.saldo == 80.0

    def test_se_puede_depositar_luego_de_un_retiro_fallido(self):
        cuenta = CuentaBancaria("Agustina Paz", saldo_inicial=40.0)
        with pytest.raises(SaldoInsuficienteError):
            cuenta.retirar(500.0)
        cuenta.depositar(100.0)
        assert cuenta.saldo == 140.0

    def test_el_saldo_no_se_puede_asignar_directamente(self):
        cuenta = CuentaBancaria("Usuario Test", saldo_inicial=100.0)
        with pytest.raises(AttributeError):
            cuenta.saldo = 99999.0
```

### Resumen del ciclo TDD aplicado
1. **Rojo:** se escribió cada prueba antes que su implementación (empezando por la creación de la cuenta y el saldo).
2. **Verde:** se implementó únicamente el código necesario en `cuenta_bancaria.py` para que cada prueba pasara.
3. **Refactor:** `transferir()` reutiliza `retirar()` y `depositar()` para no duplicar validaciones, y `saldo` se expuso como propiedad de solo lectura para evitar modificaciones directas del estado interno.
4. **Cobertura:** se cubrieron casos límite (montos en cero o negativos, saldo insuficiente, cuenta destino inexistente) y escenarios combinados (cadenas de operaciones) para asegurar consistencia del sistema completo.
