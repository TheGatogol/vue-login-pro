# Automation.md

Este archivo contiene los casos de prueba funcionales y de propiedades para el login profesional en Vue.

---

## Casos de prueba Login

1. En el input "username" ingresa un solo carácter y haz clic en "Iniciar Sesión". Valida que debajo del campo se muestre el mensaje: "El usuario debe contener mínimo 2 caracteres.".
2. En el input "username" ingresa 21 caracteres y haz clic en "Iniciar Sesión". Valida que debajo del campo se muestre el mensaje: "El usuario debe contener máximo 20 caracteres.".
3. En el input "username" ingresa caracteres especiales (por ejemplo: "admin@123") y haz clic en "Iniciar Sesión". Valida que debajo del campo se muestre el mensaje: "El usuario solo puede contener letras y números, sin espacios ni símbolos.".
4. En el input "username" ingresa "admin123456" y no ingreses error. Valida que no se muestre ningún mensaje de error debajo del campo.
5. En el input "userpassword" ingresa 5 caracteres y haz clic en "Iniciar Sesión". Valida que debajo del campo se muestre el mensaje: "La contraseña debe contener mínimo 6 caracteres.".
6. En el input "userpassword" ingresa 21 caracteres y haz clic en "Iniciar Sesión". Valida que debajo del campo se muestre el mensaje: "La contraseña debe contener máximo 20 caracteres.".
7. En el input "userpassword" ingresa "123456" y no ingreses error. Valida que no se muestre ningún mensaje de error debajo del campo.
8. Haz clic en el botón de mostrar contraseña y valida que el tipo de input cambie a texto.
9. Haz clic en el botón de ocultar contraseña y valida que el tipo de input cambie a password.
10. Ingresa usuario "admin123456" y contraseña "admin123456" y haz clic en "Iniciar Sesión". Valida que redirija a la vista de dashboard.
11. Ingresa usuario "admin123456" y contraseña "123456" y haz clic en "Iniciar Sesión". Valida que NO redirija y que debajo del campo contraseña se muestre el mensaje: "Contraseña incorrecta. Debe ser \"admin123456\".".
12. Ingresa usuario "usuarioX" y contraseña "admin123456" y haz clic en "Iniciar Sesión". Valida que NO redirija y que debajo del campo usuario se muestre el mensaje: "Usuario incorrecto. Debe ser \"admin123456\".".
13. Haz clic en el link "¿Olvidaste tu contraseña?" y valida que redirija a la vista de recuperación.

## Casos de prueba Recuperar Contraseña

14. En el input "email" ingresa 4 caracteres y haz clic en "Enviar". Valida que debajo del campo se muestre el mensaje: "El correo debe contener mínimo 5 caracteres.".
15. En el input "email" ingresa 51 caracteres y haz clic en "Enviar". Valida que debajo del campo se muestre el mensaje: "El correo debe contener máximo 50 caracteres.".
16. En el input "email" ingresa un correo inválido (por ejemplo: "correo@com") y haz clic en "Enviar". Valida que debajo del campo se muestre el mensaje: "El formato del correo es inválido. Ejemplo: usuario@dominio.com".
17. En el input "email" ingresa "test@correo.com" y no ingreses error. Valida que no se muestre ningún mensaje de error debajo del campo.
18. Haz clic en el botón "Enviar" con correo válido y valida que aparezca el mensaje de éxito.
19. Haz clic en el botón "Enviar" con correo inválido y valida que muestre el mensaje de error.
20. Haz clic en el link "Volver al login" y valida que redirija correctamente.

## Casos de prueba Dashboard

21. Valida que al ingresar a la vista de dashboard se muestre el header con el texto "Dashboard".
22. Valida que al ingresar a la vista de dashboard se muestre el botón "Cerrar sesión".
23. Haz clic en el botón "Cerrar sesión" y valida que aparezca el modal de confirmación.
24. En el modal de confirmación haz clic en "No" y valida que el modal se cierre y permanezcas en dashboard.
25. En el modal de confirmación haz clic en "Sí" y valida que redirija al login.
