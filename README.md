# CapsuleCorp – Plataforma de Reservas de Habitaciones Cápsula

## Descripción del proyecto
**CapsuleCorp** es una plataforma web destinada a gestionar reservas de *habitaciones cápsula* en un hotel moderno enfocado en viajeros que buscan comodidad, privacidad y tecnología a bajo coste.  
El proyecto forma parte del desarrollo web del curso y servirá como base para aprender HTML, CSS, JavaScript y otras tecnologías.

## Público objetivo
- Viajeros de bajo presupuesto  
- Estudiantes  
- Turistas que solo necesitan un espacio cómodo para descansar  
- Personas que prefieren estancias automatizadas y rápidas  

## Funcionalidades principales
- **Reserva online** de cápsulas por horas o días  
- Sistema de *login* y registro de usuarios  
- Selección de tipos de cápsulas  
- Gestión de reservas  
- Sección informativa sobre servicios y normas del hotel  

## Tecnologías previstas
### Frontend
- HTML5  
- CSS3  
- JavaScript  
- Diseño responsivo
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CapsuleCorp - Reservas</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f2f2f2;
            margin: 0;
            padding: 0;
        }

        header {
            background: #0a84ff;
            padding: 20px;
            color: white;
            text-align: center;
        }

        .capsule-list {
            max-width: 900px;
            margin: 40px auto;
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 25px;
        }

        .capsule {
            background: white;
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            text-align: center;
        }

        .capsule button {
            background: #0a84ff;
            border: none;
            padding: 10px 15px;
            color: white;
            border-radius: 8px;
            cursor: pointer;
        }

        .capsule button:hover {
            background: #006edc;
        }
    </style>
</head>
<body>
    <header>
        <h1>CapsuleCorp – Reserva tu cápsula de descanso</h1>
    </header>

    <section class="capsule-list">
        <div class="capsule">
            <h3>Cápsula Individual</h3>
            <p>Perfecta para descansar o trabajar con privacidad.</p>
            <button onclick="reservar('Individual')">Reservar</button>
        </div>

        <div class="capsule">
            <h3>Cápsula Doble</h3>
            <p>Ideal para parejas o descansos acompañados.</p>
            <button onclick="reservar('Doble')">Reservar</button>
        </div>

        <div class="capsule">
            <h3>Cápsula Premium</h3>
            <p>Incluye iluminación inteligente, sonido envolvente y más.</p>
            <button onclick="reservar('Premium')">Reservar</button>
        </div>
    </section>

    <script>
        function reservar(tipo) {
            alert("Has seleccionado una cápsula: " + tipo);
            // Futuro: aquí se enviará la reserva al backend
        }
    </script>
</body>
</html>
 

### Backend
- (Previsto) Node.js o PHP  
- Base de datos MySQL  
// Backend - CapsuleCorp: API de reservas de cápsulas
const express = require("express");
const app = express();
const PORT = 3000;

// Middleware para leer JSON
app.use(express.json());

// Datos simulados de cápsulas
let capsulas = [
    { id: 1, tipo: "Individual", disponible: true },
    { id: 2, tipo: "Doble", disponible: true },
    { id: 3, tipo: "Premium", disponible: false }
];

// Obtener lista de cápsulas
app.get("/api/capsulas", (req, res) => {
    res.json(capsulas);
});

// Crear una reserva
app.post("/api/reservar", (req, res) => {
    const { tipo } = req.body;

    const encontrada = capsulas.find(c => c.tipo === tipo && c.disponible);

    if (!encontrada) {
        return res.status(400).json({ mensaje: "No hay cápsulas disponibles de este tipo." });
    }

    encontrada.disponible = false;

    res.json({
        mensaje: "Reserva completada",
        capsula: encontrada
    });
});

// Iniciar servidor
app.listen(PORT, () => {
    console.log(`Servidor CapsuleCorp en funcionamiento en http://localhost:${PORT}`);
});

## Características del proyecto (lista no numerada)
- Interfaz limpia y moderna  
- Reservas rápidas  
- Información clara del hotel cápsula  
- Experiencia de usuario simplificada  

## Fases del desarrollo (lista numerada)
1. Diseño de la estructura y páginas principales  
2. Creación de estilos CSS  
3. Implementación de funciones básicas con JavaScript  
4. Integración del sistema de reservas  
5. Documentación final  

## Cita inspiradora
> “Un espacio pequeño puede ofrecer grandes experiencias si está bien diseñado.”

## Página de ejemplo parecida a mi idea
[Visita Google](https://www.airbnb.es/?_set_bev_on_new_domain=1764787238_EAOWY5MjRjZjYxN2&set_everest_cookie_on_new_domain=1764787238.EAYzhhMGE5MzhmNjRlMW.Ah3VYpKajweU4ib6sLhFXByANqD0CEI9w9zQPYia6to)

## Imágen desde URL externa
![Ejemplo de como sería la cápsula](https://imgs.search.brave.com/JyvexQQ_c9zJkNoU9YPSVFKAZE3QTkclD68FSI7Am5c/rs:fit:500:0:1:0/g:ce/aHR0cHM6Ly9ibG9n/LmNlbnRyYWxkZXJl/c2VydmFzLmNvbS93/cC1jb250ZW50L3Vw/bG9hZHMvMjAyNC8x/MC9PWFlHRU4tSE9T/VEVMLUNhcHN1bGEu/cG5n)

## Boceto de la interfaz

Aquí puedes ver el primer diseño de la interfaz principal:
![Logo Ejemplo](/proyecto intermodular/6173.JPG "Logo")
