# Difference between Spring MVC formatters and converters

Converters are used to convert one Java type to another Java type. For example, 
from Long to java.util.Date or from Integer to Color or from String to Date. 
It can be used in the web tier or any other tier that needs conversion service.

<b>Formatters are used to convert String to another Java type and back. </b>
So, one type must be String. You cannot, for example, write a formatter that converts a Long to a Date. 
Examples of formatters are DateFormatter, for parsing String to java.util.Date and formatting a Date. 
In addition, formatters' messages can be localized.

来源: https://stackoverflow.com/questions/13048368/difference-between-spring-mvc-formatters-and-converters
