# Date/Time en Java  #

## Introducción ##

Java tiene una clase llamada "java.util.Date" que representa un punto específico en el tiempo con milisegundos de precisión. Puede usar esta clase para trabajar con fechas y horas en su código. También hay una clase "java.util.Calendar" que proporciona una forma de manipular y formatear fechas. Además, desde Java 8, se ha introducido una nueva API de fecha y hora, llamada "java.time", que proporciona una mayor claridad y funcionalidad en comparación con las clases anteriores.

## Métodos  Date/Time y Calendar ##

A continuación se presentan algunos de los métodos más utilizados de las clases "java.util.Date" y "java.util.Calendar" en Java, junto con ejemplos de su uso:

```
    Date.getTime(): devuelve el número de milisegundos desde la época (1 de enero de 1970, 00:00:00 UTC) hasta la fecha representada por el objeto Date.
```

```
Date fechaActual = new Date();
long milisegundos = fechaActual.getTime();
System.out.println("Milisegundos desde la época: " + milisegundos);
```

    Calendar.get(Calendar.YEAR): devuelve el año representado por el objeto Calendar.

```
Calendar fechaActual = Calendar.getInstance();
int anio = fechaActual.get(Calendar.YEAR);
System.out.println("Año actual: " + anio);
```

    Calendar.set(Calendar.YEAR, 2021): establece el año representado por el objeto Calendar en el valor especificado.

```
Calendar fecha = Calendar.getInstance();
fecha.set(Calendar.YEAR, 2021);
System.out.println("Año establecido: " + fecha.get(Calendar.YEAR));
```

    Calendar.add(Calendar.DATE, 1): agrega la cantidad especificada de días a la fecha representada por el objeto Calendar.

```
Calendar fecha = Calendar.getInstance();
fecha.add(Calendar.DATE, 1);
System.out.println("Fecha en un día: " + fecha.getTime());
```

    DateFormat.format(date): devuelve una cadena que representa la fecha especificada en el formato de fecha y hora especificado.

```
Date fechaActual = new Date();
DateFormat formatoFecha = new SimpleDateFormat("dd/MM/yyyy");
String fechaFormateada = formatoFecha.format(fechaActual);
System.out.println("Fecha Formateada: " + fechaFormateada);
```

Ten en cuenta que estos son solo algunos ejemplos de los métodos disponibles en las clases mencionadas. Hay muchos otros métodos y opciones para trabajar con fechas y horas en Java.

## Librería java.time ##

La librería "java.time" en Java 8 proporciona una nueva API de fecha y hora con una mayor claridad y funcionalidad en comparación con las clases de fecha y hora anteriores. A continuación se presentan algunos de los tipos y métodos más comunes de esta librería, junto con ejemplos de su uso:

    LocalDate: representa una fecha sin hora ni zona horaria, como "2022-12-03".

```
LocalDate fechaActual = LocalDate.now();
System.out.println("Fecha actual: " + fechaActual);
```

    LocalTime: representa una hora sin fecha ni zona horaria, como "10:15:30".

```
LocalTime horaActual = LocalTime.now();
System.out.println("Hora actual: " + horaActual);
```

    LocalDateTime: representa una fecha y hora sin zona horaria, como "2022-12-03T10:15:30".

```
LocalDateTime fechaHoraActual = LocalDateTime.now();
System.out.println("Fecha y hora actual: " + fechaHoraActual);
```

    ZonedDateTime: representa una fecha y hora con zona horaria, como "2022-12-03T10:15:30+01:00[Europe/Paris]".

```
ZonedDateTime fechaHoraZonaActual = ZonedDateTime.now();
System.out.println("Fecha, hora y zona actual: " + fechaHoraZonaActual);
```

    Duration: representa una duración de tiempo en unidades de segundos y nanosegundos.

```
Duration duracion = Duration.ofMinutes(60);
System.out.println("Duración de 60 minutos: " + duracion);
```

    Period: representa una cantidad de tiempo en unidades de años, meses y días.

```
Period periodo = Period.of(1, 2, 3);
System.out.println("Periodo de 1 año, 2 meses y 3 días: " + periodo);
```

    LocalDate.of(2022,12,3): devuelve un objeto LocalDate para la fecha especificada.

```
LocalDate fechaEspecifica = LocalDate.of(2022, 12, 3);
System.out.println("Fecha específica: " + fechaEspecifica);
```

    LocalDate.parse("2022-12-03"): devuelve un objeto LocalDate a partir de una cadena en el formato ISO_LOCAL_DATE.

```
LocalDate fechaParseada = LocalDate.parse("2022-12-03");
System.out.println("Fecha parseada: " + fechaParseada
```

https://www.tutorialspoint.com/java/java_date_time.htm

https://docs.oracle.com/javase/8/docs/api/java/time/package-summary.html

https://www.baeldung.com/java-8-date-time-intro


## Ejercicios ##

Aquí hay algunos ejercicios que puedes usar para practicar la librería java.time en Java:

    Escribir una función que imprima la fecha y hora actual en varios formatos diferentes, como "dd/MM/yyyy", "MM/dd/yyyy" y "yyyy-MM-dd HH:mm:ss".

    Escribir una función que calcule la diferencia entre dos fechas especificadas en días, meses y años.

    Escribir una función que calcule la fecha de la semana siguiente, de la siguiente y de la siguiente semana.

    Escribir una función que calcule la fecha de Navidad en el año actual y en el próximo año.

    Escribir una función que calcule la diferencia entre la fecha actual y una fecha de cumpleaños especificada en años, meses y días.

    Escribir una función que calcule el número de días que quedan hasta el próximo día festivo especificado (como Año Nuevo, Navidad, etc.).

    Escribir una función que dada una fecha y una duración en segundos, devuelva la fecha y hora resultante.

    Escribir una función que calcule la fecha y hora en una zona horaria específica (como UTC, Europe/Paris, America/New_York, etc.)

    Escribir una función que calcule la fecha y hora en la que se alcanza un número específico de días, horas, minutos y segundos en el futuro.

    Escribir una función que dada una fecha y una duración en horas, minutos y segundos, devuelva la fecha y hora resultante.

Recuerda que estos son solo algunos ejemplos y que puedes ser creativo y pensar en otros ejercicios para practicar la librería java.time.