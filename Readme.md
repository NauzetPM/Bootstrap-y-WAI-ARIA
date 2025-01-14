# Ejemplos de uso de WAI-ARIA en elementos Bootsrap
## Elemento 1: Botón
Código original (Bootstrap):
```html
<button type="button" class="btn btn-primary">Enviar</button>
```
Código mejorado con WAI-ARIA:
```html
<button type="button" class="btn btn-primary" role="button" aria-label="Enviar formulario">Enviar</button>
```
Explicación:
role="button": Aunque el botón ya tiene el papel de "botón", especificarlo explícitamente mejora la accesibilidad.
aria-label="Enviar formulario": Proporciona una descripción más clara para los usuarios de lectores de pantalla, especificando que el botón es para "enviar formulario", en lugar de solo "enviar".

## Elemento 2: Modal
Código original (Bootstrap):
```html
<div class="modal" tabindex="-1">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title">Título del modal</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Cerrar"></button>
      </div>
      <div class="modal-body">
        <p>Contenido del modal...</p>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
        <button type="button" class="btn btn-primary">Guardar cambios</button>
      </div>
    </div>
  </div>
</div>
```
Código mejorado con WAI-ARIA:
```html
<div class="modal" tabindex="-1" role="dialog" aria-labelledby="modalTitle" aria-describedby="modalDescription">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="modalTitle">Título del modal</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Cerrar"></button>
      </div>
      <div class="modal-body" id="modalDescription">
        <p>Contenido del modal...</p>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
        <button type="button" class="btn btn-primary">Guardar cambios</button>
      </div>
    </div>
  </div>
</div>
```
Explicación:

role="dialog": Indica que el elemento es un cuadro de diálogo, lo que ayuda a los usuarios con tecnologías asistivas a identificarlo correctamente.
aria-labelledby="modalTitle": Asocia el título del modal con el elemento de encabezado para mejorar la navegación del lector de pantalla.
aria-describedby="modalDescription": Proporciona una descripción del contenido del modal, lo cual es útil para los usuarios que necesitan más contexto.

## Elemento 3: Menú desplegable
Código original (Bootstrap):
```html
<div class="dropdown">
  <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton" data-bs-toggle="dropdown" aria-expanded="false">
    Opciones
  </button>
  <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton">
    <li><a class="dropdown-item" href="#">Acción</a></li>
    <li><a class="dropdown-item" href="#">Otra acción</a></li>
    <li><a class="dropdown-item" href="#">Algo más aquí</a></li>
  </ul>
</div>
```
Código mejorado con WAI-ARIA:
```html
<div class="dropdown">
  <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton" data-bs-toggle="dropdown" aria-expanded="false" aria-controls="dropdownMenu">
    Opciones
  </button>
  <ul class="dropdown-menu" id="dropdownMenu" aria-labelledby="dropdownMenuButton" role="menu">
    <li><a class="dropdown-item" href="#" role="menuitem">Acción</a></li>
    <li><a class="dropdown-item" href="#" role="menuitem">Otra acción</a></li>
    <li><a class="dropdown-item" href="#" role="menuitem">Algo más aquí</a></li>
  </ul>
</div>
```
Explicación:

aria-expanded="false": Este atributo indica si el menú está desplegado o no, proporcionando contexto adicional a los usuarios de tecnologías asistivas.
aria-controls="dropdownMenu": Relaciona el botón con el menú desplegable para indicar que el botón controla la visibilidad del menú.
role="menu" y role="menuitem": Estos roles son necesarios para definir el propósito del menú y sus elementos, mejorando la navegación y la comprensión del contenido.

## Elemento 4: Alerta
Código original (Bootstrap):
```html
<div class="alert alert-warning" role="alert">
  Este es un mensaje de alerta.
</div>
```
Código mejorado con WAI-ARIA:
```html
<div class="alert alert-warning" role="alert" aria-live="assertive" aria-atomic="true">
  Este es un mensaje de alerta.
</div>
```
Explicación:

aria-live="assertive": Indica que la alerta debe ser anunciada de inmediato por el lector de pantalla, mejorando la experiencia para el usuario al recibir notificaciones importantes.
aria-atomic="true": Asegura que todo el contenido de la alerta sea anunciado como una unidad, lo que es útil para no fragmentar el mensaje de alerta.

## Elemento 5: Pestañas (Tabs)
Código original (Bootstrap):
```html
<ul class="nav nav-tabs" id="myTab" role="tablist">
  <li class="nav-item" role="presentation">
    <a class="nav-link active" id="home-tab" data-bs-toggle="tab" href="#home" role="tab" aria-controls="home" aria-selected="true">Inicio</a>
  </li>
  <li class="nav-item" role="presentation">
    <a class="nav-link" id="profile-tab" data-bs-toggle="tab" href="#profile" role="tab" aria-controls="profile" aria-selected="false">Perfil</a>
  </li>
  <li class="nav-item" role="presentation">
    <a class="nav-link" id="contact-tab" data-bs-toggle="tab" href="#contact" role="tab" aria-controls="contact" aria-selected="false">Contacto</a>
  </li>
</ul>
<div class="tab-content" id="myTabContent">
  <div class="tab-pane fade show active" id="home" role="tabpanel" aria-labelledby="home-tab">Contenido de inicio...</div>
  <div class="tab-pane fade" id="profile" role="tabpanel" aria-labelledby="profile-tab">Contenido de perfil...</div>
  <div class="tab-pane fade" id="contact" role="tabpanel" aria-labelledby="contact-tab">Contenido de contacto...</div>
</div>
```
Código mejorado con WAI-ARIA:
```html
<ul class="nav nav-tabs" id="myTab" role="tablist" aria-label="Pestañas de navegación">
  <li class="nav-item" role="presentation">
    <a class="nav-link active" id="home-tab" data-bs-toggle="tab" href="#home" role="tab" aria-controls="home" aria-selected="true" aria-labelledby="home-tab">Inicio</a>
  </li>
  <li class="nav-item" role="presentation">
    <a class="nav-link" id="profile-tab" data-bs-toggle="tab" href="#profile" role="tab" aria-controls="profile" aria-selected="false" aria-labelledby="profile-tab">Perfil</a>
  </li>
  <li class="nav-item" role="presentation">
    <a class="nav-link" id="contact-tab" data-bs-toggle="tab" href="#contact" role="tab" aria-controls="contact" aria-selected="false" aria-labelledby="contact-tab">Contacto</a>
  </li>
</ul>
<div class="tab-content" id="myTabContent">
  <div class="tab-pane fade show active" id="home" role="tabpanel" aria-labelledby="home-tab">Contenido de inicio...</div>
  <div class="tab-pane fade" id="profile" role="tabpanel" aria-labelledby="profile-tab">Contenido de perfil...</div>
  <div class="tab-pane fade" id="contact" role="tabpanel" aria-labelledby="contact-tab">Contenido de contacto...</div>
</div>
```
Explicación:

aria-label="Pestañas de navegación": Proporciona una descripción del conjunto de pestañas, útil para usuarios de lectores de pantalla.
aria-labelledby: Asocia cada contenido con el identificador de la pestaña correspondiente para mejorar la navegación entre las pestañas.