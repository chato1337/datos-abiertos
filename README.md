# datos.gov.co para Laravel

[![Latest Version on Packagist](https://img.shields.io/packagist/v/andreshg112/datos-abiertos.svg?style=flat-square)](https://packagist.org/packages/andreshg112/datos-abiertos)
[![Build Status](https://img.shields.io/travis/andreshg112/datos-abiertos/master.svg?style=flat-square)](https://travis-ci.org/andreshg112/datos-abiertos)
[![Quality Score](https://img.shields.io/scrutinizer/g/andreshg112/datos-abiertos.svg?style=flat-square)](https://scrutinizer-ci.com/g/andreshg112/datos-abiertos)
[![Total Downloads](https://img.shields.io/packagist/dt/andreshg112/datos-abiertos.svg?style=flat-square)](https://packagist.org/packages/andreshg112/datos-abiertos)

Este paquete encapsula las consultas a la API de [Datos Abiertos del Gobierno de Colombia](datos.gov.co).

## Recursos implementados

-   [Códigos de la Divisón Político-Administrativa del país (Divipola)](https://dev.socrata.com/foundry/www.datos.gov.co/gdxc-w37w).

> Si deseas que desarrolle una consulta a otro recurso de datos.gov.co, puedes realizar la petición en los [Issues](issues).

## Requisitos

-   Laravel >= 5.5
-   PHP >= 7.x.x

> Si quieres soporte para una versión inferior a las especificadas, por favor deja la petición en los [Issues](issues) y veré qué puedo hacer.

## Instalación

Puedes instalar el paquete a través de composer:

```bash
composer require andreshg112/datos-abiertos
```

Este paquete usa [Laravel Package Discovery](https://laravel.com/docs/5.5/packages#package-discovery) por lo que, si usas Laravel 5.5 o superior, no debes preocuparte agregar `\Andreshg112\DatosAbiertos\DatosAbiertosServiceProvider` al listado de `providers` en el archivo `config/app.php`.

## Uso

### Uso básico

```php
use Andreshg112\DatosAbiertos\Facades\Divipola;

// Listado total de municipios:
$data = Divipola::getData();

// Para consultar por código de municipio:
$data = Divipola::getByCodMpio($codMpio);
```

### Uso de filtros

> En la [definición de la API de Divipola](https://dev.socrata.com/foundry/www.datos.gov.co/gdxc-w37w) puedes encontrar los detalles del recurso y el uso de filtros.

```php
use Andreshg112\DatosAbiertos\Facades\Divipola;

// Para filtrar por código de departamento puedes hacer cualquiera de las siguientes formas:

$filterOrSoqlQuery = 'cod_depto=20';

$filterOrSoqlQuery = ['cod_depto' => '20'];

$data = Divipola::getData($filterOrSoqlQuery);
```

> Este paquete usa [allejo/php-soda](https://github.com/allejo/PhpSoda) para realizar las peticiones a los recursos de datos.gov.co usando Socrata Open Data API (SODA), por lo tanto `$filterOrSoqlQuery` puede ser cualquiera de los parámetros aceptados por la función `\allejo\Socrata\SodaDataset::getData(filterOrSoqlQuery)`. Para usar filtros avanzados, dirígete a su [documentación](https://github.com/allejo/PhpSoda/wiki/Simple-Filters) (en inglés).

### Pruebas

```bash
composer test
```

### Registro de cambios

Por favor, mira el listado de [Versiones](releases) para obtener más información sobre lo que ha cambiado recientemente.

## Contribuir

Por favor, mira el archivo [CONTRIBUTING](CONTRIBUTING.md) (en inglés) para más detalles.

### Seguridad

Si descubres una vulnerabilidad o fallo relacionado con seguridad, te agradezco que por favor me escribas a andreshg112@gmail.com en vez de hacerlo en el registro de errores.

## Créditos

-   [Andrés Herrera García](https://github.com/andreshg112)
-   [All Contributors](../../contributors)

## Licencia

Licencia MIT. Por favor, mira el archivo [License File](LICENSE.md) (en inglés) para más información.

## Laravel Package Boilerplate

Este paquete fue generado usando [Laravel Package Boilerplate](https://laravelpackageboilerplate.com).