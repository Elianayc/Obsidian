```mermaid

%%{init: {

    'theme': 'dark',

    'themeVariables': {

                        'background': '#121212',

                        'lineColor': '#a5d7f7',

                        'fontFamily': 'Cascadia Code, Fira Code, Consolas, Courier New, monospace',

                        'fontSize': '14px'

        },

        'themeCSS': 'path { stroke-width: 1.5px !important; }'

    } }%%

  

classDiagram

  

class Nivel {

    <<enumeration>>

    Baja

    Media

    Alta

    Elevada

    Excelente

    Extrema

    Afectada

}

  

class Barco {

    <<abstract>>

    - nombre: string

    - flotabilidad: Nivel

    - estabilidad: Nivel

}

  

class BarcoDeGuerra {

    <<abstract>>

    - solidez: Nivel

    - potenciaFuego: Nivel

    - velocidadCrucero: number

}

class Acorazado {

    - blindaje: Nivel

}

class Destructor {

    - maniobrabilidad: Nivel

}

class BarcoHospital {

    - capacidadPacientes: number

}

class LanchaMedica {

    - motor: string

    - maniobrabilidad: Nivel

    - capacidadGruaKg: number

}

Barco <|-- BarcoDeGuerra

Barco <|-- BarcoHospital

Barco <|-- LanchaMedica

BarcoDeGuerra <|-- Acorazado

BarcoDeGuerra <|-- Destructor

  

%%Colores de las clases

classDef default fill:#362b2b,stroke:#f39bce,color:#e4dcd2

```