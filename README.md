\documentclass[12pt,a4paper]{article}
\usepackage[utf8]{inputenc}
\usepackage[spanish]{babel}
\usepackage{graphicx}
\usepackage{float}
\usepackage{hyperref}
\usepackage{geometry}
\usepackage{url}
\usepackage{amsmath}
\usepackage{amssymb}
\usepackage{array}
\usepackage{longtable}
\usepackage{booktabs}
\usepackage{multirow}
\usepackage{caption}
\usepackage{subcaption}
\usepackage{enumitem}
\usepackage{color}
\usepackage{colortbl}
\usepackage{listings}
\usepackage{xcolor}
\usepackage{titlesec}
\usepackage{fancyhdr}
\usepackage{setspace}
\usepackage{tocloft}
\usepackage{cite}
\usepackage[nottoc]{tocbibind}

% Configuración de página
\geometry{
    a4paper,
    left=2.5cm,
    right=2.5cm,
    top=2.5cm,
    bottom=2.5cm,
    headheight=1.0cm,
    footskip=1.0cm
}

% Configuración de hipervínculos - SIN COLOR
\hypersetup{
    colorlinks=false,
    linkcolor=black,
    urlcolor=black,
    citecolor=black
}

% Configuración de títulos - más compactos
\titleformat{\section}{\normalfont\large\bfseries}{\thesection}{1em}{}
\titleformat{\subsection}{\normalfont\normalsize\bfseries}{\thesubsection}{1em}{}
\titleformat{\subsubsection}{\normalfont\normalsize\bfseries}{\thesubsubsection}{1em}{}
\titlespacing*{\section}{0pt}{0.5\baselineskip}{0.3\baselineskip}
\titlespacing*{\subsection}{0pt}{0.3\baselineskip}{0.2\baselineskip}
\titlespacing*{\subsubsection}{0pt}{0.2\baselineskip}{0.1\baselineskip}

% Configuración de encabezados y pies de página
\pagestyle{fancy}
\fancyhf{}
\fancyhead[L]{\small \textit{UTEQ - ISR-401}}
\fancyhead[R]{\small \textit{SGCV-IA - MDD}}
\fancyfoot[C]{\thepage}
\renewcommand{\headrulewidth}{0.4pt}
\renewcommand{\footrulewidth}{0.4pt}

% Configuración del índice
\renewcommand{\cftsecfont}{\normalfont}
\renewcommand{\cftsecpagefont}{\normalfont}
\renewcommand{\cftsubsecfont}{\normalfont}
\renewcommand{\cftsubsecpagefont}{\normalfont}
\renewcommand{\cftfigfont}{\normalfont}
\renewcommand{\cftfigpagefont}{\normalfont}
\renewcommand{\cfttabfont}{\normalfont}
\renewcommand{\cfttabpagefont}{\normalfont}
\renewcommand{\cftdot}{.}
\renewcommand{\cftdotsep}{1}
\setlength{\cftbeforeloftitleskip}{0.5\baselineskip}
\setlength{\cftbeforelottitleskip}{0.5\baselineskip}

% Configuración de listados de código para C++
\lstset{
    language=C++,
    basicstyle=\ttfamily\scriptsize,
    keywordstyle=\color{blue}\bfseries,
    commentstyle=\color{green!60!black},
    stringstyle=\color{red},
    numbers=left,
    numberstyle=\tiny\color{gray},
    frame=single,
    breaklines=true,
    captionpos=b,
    tabsize=4,
    showspaces=false,
    showstringspaces=false
}

% Espaciado
\setstretch{1.1}

% Comandos personalizados
\newcommand{\tab}{\hspace{1cm}}

% Inicio del documento
\begin{document}

% ============================================================================
% CARÁTULA (NO CUENTA PARA EL LÍMITE DE 20 PÁGINAS)
% ============================================================================
\begin{titlepage}
    \centering
    \pagenumbering{gobble}

    \includegraphics[width=0.20\textwidth]{logo.jpg}
    \vspace{0.6cm}
    
    {\large \textbf{UNIVERSIDAD TÉCNICA ESTATAL DE QUEVEDO}}\\[0.15cm]
    {\small Facultad de Ciencias de la Computación y Diseño Digital}\\[0.1cm]
    {\small Carrera de Ingeniería en Software}

    \vspace{0.9cm}
    \rule{0.85\textwidth}{0.6pt}

    \vspace{0.6cm}
    \begin{minipage}{0.85\textwidth}
        \centering
        {\Large \textbf{EXPOSICIÓN SOBRE MODEL-DRIVEN DEVELOPMENT (MDD) CON BOUML}}\\[0.4cm]
        {\normalsize \textbf{Caso de estudio:} Sistema de Gestión Clínica Veterinaria con IA (SGCV-IA)\\
        Módulo de Gestión de Citas Médicas (Atenciones Clínicas)}
    \end{minipage}

    \vspace{0.6cm}
    \rule{0.85\textwidth}{0.6pt}

    \vspace{1.0cm}
    \begin{minipage}{0.8\textwidth}
        \centering
        \renewcommand{\arraystretch}{1.3}
        \begin{tabular}{r l}
            \textbf{Asignatura:} & Ingeniería de Requisitos (ISR-401) \\
            \textbf{Docente:} & Ing. Gleiston Guerrero Ulloa, PhD. \\
            \textbf{Nivel / Curso:} & 4to A Software \\
            \textbf{Período académico:} & 2026--2027 PPA \\
        \end{tabular}
    \end{minipage}

    \vspace{1.1cm}
    {\small \textbf{INTEGRANTES}}\\[0.35cm]
    \begin{tabular}{c}
        Arteaga Danela \\
        Herrera Thais \\
        Marcillo Jeanpool \\
        Robison Jenapierrel
    \end{tabular}

    \vfill
    {\small Quevedo -- Ecuador}\\[0.15cm]
    {\small \textbf{Fecha de entrega:} 18 de julio de 2026}
    \vspace{0.5cm}
\end{titlepage}

\pagenumbering{arabic}

% ============================================================================
% ÍNDICE (NO CUENTA PARA EL LÍMITE DE 20 PÁGINAS)
% ============================================================================
\newpage
\tableofcontents
\newpage
\listoffigures
\newpage
\listoftables

% ============================================================================
% 1. RESUMEN - Página 1
% ============================================================================
\newpage
\section*{Resumen}
\addcontentsline{toc}{section}{Resumen}

El presente trabajo aborda la aplicación de Model-Driven Development (MDD) como enfoque para el desarrollo de software, utilizando la herramienta BOUML para la generación automática de código a partir de modelos UML. El estudio se centra en el módulo de Gestión de Citas Médicas (Atenciones Clínicas) del Sistema de Gestión Clínica Veterinaria con IA (SGCV-IA), correspondiente al Proyecto Fin de Curso (PFC) del equipo. Se presenta el marco teórico que sustenta la Ingeniería Dirigida por Modelos (MDE), la Arquitectura Dirigida por Modelos (MDA), y los conceptos de PIM y PSM. Se justifica la selección de BOUML frente a otras herramientas UML como StarUML, Enterprise Architect y Visual Paradigm, destacando su naturaleza libre, ligereza y capacidades de generación de código. El trabajo incluye un manual detallado del uso de BOUML, el diseño del diagrama de clases del sistema basado en el modelo de datos del SGCV-IA (14 entidades), el proceso de generación de código en C++ (lenguaje soportado por BOUML), y la verificación del código generado. Además, se aborda el concepto de Roundtrip Engineering para mantener la sincronización entre el modelo y el código. El contenido se encuentra disponible en un repositorio público de GitHub, organizado según las buenas prácticas de documentación.

\noindent\textbf{Palabras clave:} MDD, BOUML, UML, Generación de Código, Roundtrip Engineering, SGCV-IA, C++.

% ============================================================================
% 2. INTRODUCCIÓN - Página 2
% ============================================================================
\newpage
\section{Introducción}

\subsection{Contexto y Motivación}

En el contexto actual de la ingeniería de software, la complejidad de los sistemas y la necesidad de acelerar los ciclos de desarrollo han impulsado la adopción de enfoques que elevan el nivel de abstracción en el proceso de construcción de software. La Ingeniería Dirigida por Modelos (MDE) propone que los modelos, más que el código, sean los artefactos primarios del desarrollo, permitiendo la generación automática de implementaciones a partir de especificaciones formales \cite{schmidt2006}. Esta filosofía, materializada en la Arquitectura Dirigida por Modelos (MDA) de la Object Management Group (OMG), busca separar la lógica de negocio de los detalles de la plataforma tecnológica, mejorando la portabilidad, la interoperabilidad y la productividad \cite{omg2014}.

El Model-Driven Development (MDD) se presenta como una aplicación práctica de estos principios, donde los modelos UML se transforman sistemáticamente en código ejecutable. Este enfoque no solo acelera el desarrollo, sino que también reduce errores y mantiene la trazabilidad entre el diseño y la implementación \cite{selic2003}. En este marco, las herramientas CASE juegan un papel fundamental. BOUML, una herramienta de modelado UML libre y multiplataforma, destaca por su velocidad y capacidad para generar código en múltiples lenguajes, incluyendo C++ \cite{bouml}.

\subsection{Problemática del Desarrollo Tradicional}

El desarrollo de software tradicional enfrenta diversos desafíos que el MDD busca resolver:

\begin{itemize}
    \item \textbf{Brecha semántica:} Dificultad para mantener la coherencia entre los requisitos, el diseño y la implementación, lo que genera inconsistencias y errores difíciles de rastrear.
    \item \textbf{Documentación obsoleta:} Los documentos de diseño tienden a desactualizarse rápidamente, perdiendo su valor como guía para el desarrollo y mantenimiento.
    \item \textbf{Productividad limitada:} El código repetitivo (getters, setters, constructores, etc.) consume tiempo valioso que podría dedicarse a la lógica de negocio.
    \item \textbf{Errores de implementación:} La traducción manual del diseño al código introduce errores humanos, especialmente en sistemas complejos.
\end{itemize}

\subsection{Objetivo del Trabajo}

El presente trabajo se enmarca en la asignatura de Ingeniería de Requisitos y tiene como objetivo demostrar la aplicación práctica de MDD utilizando BOUML, tomando como caso de estudio el módulo de Gestión de Citas Médicas del Sistema de Gestión Clínica Veterinaria con IA (SGCV-IA), que constituye el Proyecto Fin de Curso (PFC) del equipo.

\subsection{Estructura del Documento}

Este documento se organiza en las siguientes secciones: Marco Teórico, Justificación de la Herramienta, Descripción del PFC, Modelo UML, Configuración del Generador, Proceso de Generación, Verificación del Código, Roundtrip Engineering, Distribución del Trabajo, Conclusiones y Referencias.

% ============================================================================
% 3. MARCO TEÓRICO - Páginas 3-6
% ============================================================================
\newpage
\section{Marco Teórico}

\subsection{Ingeniería Dirigida por Modelos (MDE)}

La Ingeniería Dirigida por Modelos (Model-Driven Engineering - MDE) es un paradigma de desarrollo de software que utiliza modelos como los artefactos principales en todas las fases del ciclo de vida del software \cite{schmidt2006}. 

\subsubsection{Principios Fundamentales de MDE}

\begin{enumerate}
    \item \textbf{Modelos como artefactos de primera clase:} Los modelos no son solo documentación, sino que son la fuente autoritativa del sistema. Son elementos ejecutables o transformables que guían todo el proceso de desarrollo.
    \item \textbf{Transformaciones automatizadas:} La generación de código y otros artefactos se realiza mediante transformaciones automáticas, reduciendo la intervención manual y los errores asociados.
    \item \textbf{Abstracción:} Los modelos permiten trabajar con conceptos del dominio sin preocuparse por detalles de implementación, facilitando la comunicación entre stakeholders.
\end{enumerate}

El objetivo central de la MDE es elevar el nivel de abstracción en el desarrollo, permitiendo a los ingenieros trabajar con conceptos del dominio del problema en lugar de lidiar con los detalles de implementación de una plataforma específica. Este enfoque promete mejorar la productividad y la calidad del software \cite{pohl2025}.

\subsection{Model Driven Architecture (MDA)}

La Arquitectura Dirigida por Modelos (Model Driven Architecture - MDA) es una iniciativa de la OMG lanzada en 2001 para estandarizar y guiar la aplicación de la MDE \cite{omg2014}. Sus pilares fundamentales son:

\begin{itemize}
    \item \textbf{Meta-Object Facility (MOF):} Define la infraestructura para crear metamodelos, proporcionando un estándar para la definición de lenguajes de modelado.
    \item \textbf{Unified Modeling Language (UML):} Lenguaje de modelado visual estándar para la especificación, visualización, construcción y documentación de sistemas de software.
    \item \textbf{XML Metadata Interchange (XMI):} Estándar para el intercambio de modelos entre diferentes herramientas, facilitando la interoperabilidad.
\end{itemize}

\subsubsection{Modelos CIM, PIM y PSM}

La arquitectura MDA se estructura en torno a tres niveles de abstracción \cite{omg2014}:

\begin{enumerate}
    \item \textbf{Computation Independent Model (CIM):} Describe los requisitos del sistema y la lógica de negocio sin considerar su implementación tecnológica. Se enfoca en el "qué" debe hacer el sistema y es comprensible para los expertos del dominio.
    \item \textbf{Platform Independent Model (PIM):} Es un modelo del sistema que especifica su funcionalidad y estructura, pero sin detalles de la plataforma tecnológica. Representa el "cómo" a nivel de diseño y es independiente de la implementación.
    \item \textbf{Platform Specific Model (PSM):} Es un modelo del sistema adaptado a una plataforma tecnológica concreta. Añade detalles de implementación específicos como el framework de persistencia, el middleware o el lenguaje de programación.
\end{enumerate}

\subsection{Model-Driven Development (MDD)}

El Model-Driven Development (MDD) es la aplicación práctica de los principios de MDE/MDA en el proceso de desarrollo de software \cite{selic2003}. El proceso de MDD se apoya en dos tipos fundamentales de transformaciones \cite{omg2008}:

\subsubsection{Transformaciones Modelo a Modelo (M2M)}

Las transformaciones M2M producen un modelo destino a partir de uno de origen, ambos conformes a metamodelos. El estándar OMG de referencia es QVT (Query/View/Transformation) \cite{omg2016}. Un ejemplo típico es la transformación de un PIM a un PSM, donde se añaden detalles de implementación específicos de la plataforma.

\subsubsection{Transformaciones Modelo a Texto (M2T)}

Las transformaciones M2T producen artefactos textuales (código fuente, configuraciones, documentación) a partir de un modelo. El estándar OMG de referencia es MOFM2T (MOF Model To Text) \cite{omg2008}. Estas transformaciones son el paso final que genera código ejecutable a partir del modelo.

\subsection{UML (Unified Modeling Language)}

UML es un lenguaje de modelado visual de propósito general, estandarizado por la OMG \cite{omg2017}. Proporciona una notación gráfica para representar diferentes aspectos de un sistema a través de diversos tipos de diagramas:

\begin{itemize}
    \item \textbf{Diagramas Estructurales:} Clases, Componentes, Despliegue, Objetos, Paquetes, Estructura Compuesta, Perfiles.
    \item \textbf{Diagramas de Comportamiento:} Casos de Uso, Actividades, Máquinas de Estados, Secuencia, Comunicación, Tiempo, Interacción General.
\end{itemize}

En el contexto de MDD, UML es el lenguaje principal para construir los modelos PIM y PSM \cite{pohl2025}.

\subsection{Modelado de Requisitos y MDD}

La especificación de requisitos se rige por la norma IEEE/ISO/IEEE 29148:2018 \cite{ieee29148}. Esta norma establece que la calidad de un SRS se evalúa según cuatro atributos: completitud, consistencia, verificabilidad y trazabilidad.

Las tres perspectivas de modelado son complementarias y ninguna es suficiente por sí sola \cite{pohl2025}:

\begin{itemize}
    \item \textbf{Modelo de Datos:} Responde a "¿qué existe en el sistema?". Representa las entidades y sus relaciones a través de diagramas ER y de clases.
    \item \textbf{Modelo Funcional:} Responde a "¿cómo se transforman esos datos?". Representa los procesos y flujos de datos mediante DFD y diagramas de actividades.
    \item \textbf{Modelo de Comportamiento:} Responde a "¿cuándo y en qué orden ocurren esas transformaciones?". Representa los estados y transiciones mediante máquinas de estados y diagramas de secuencia.
\end{itemize}

\subsection{Ingeniería Directa, Inversa y Roundtrip}

La gestión de la relación entre el modelo y el código se aborda mediante tres conceptos fundamentales \cite{pohl2025}:

\subsubsection{Ingeniería Directa (Forward Engineering)}

Es el proceso tradicional de generar código a partir de un modelo. Se parte del diseño UML y se obtiene el código fuente en el lenguaje de programación deseado. Es el flujo principal en MDD y permite mantener la coherencia entre el diseño y la implementación.

\subsubsection{Ingeniería Inversa (Reverse Engineering)}

Es el proceso inverso. Se parte del código fuente existente y se genera o actualiza un modelo UML que lo represente. Es útil para documentar sistemas legados o para incorporar código escrito manualmente al proceso de modelado.

\subsubsection{Roundtrip Engineering}

El Roundtrip Engineering es la capacidad de una herramienta de soportar tanto la ingeniería directa como la inversa de manera iterativa, manteniendo la consistencia entre el modelo y el código \cite{pohl2025}. Su característica clave es la sincronización incremental: no se trata simplemente de regenerar todo, sino de fusionar los cambios realizados en el modelo o en el código sin perder el trabajo realizado en el otro artefacto.

\subsection{Beneficios y Limitaciones del MDD}

\subsubsection{Beneficios}

\begin{itemize}
    \item \textbf{Aumento de la productividad:} Automatización de tareas repetitivas, reduciendo el tiempo de desarrollo.
    \item \textbf{Mejora de la calidad:} El código generado es consistente con el modelo, reduciendo errores.
    \item \textbf{Portabilidad:} El mismo PIM puede generar múltiples PSMs para diferentes plataformas.
    \item \textbf{Documentación viva:} El modelo se mantiene sincronizado con el código, evitando la obsolescencia.
    \item \textbf{Trazabilidad:} Facilita el rastreo entre requisitos, diseño y código.
\end{itemize}

\subsubsection{Limitaciones}

\begin{itemize}
    \item \textbf{Curva de aprendizaje:} Requiere formación en herramientas y conceptos de modelado.
    \item \textbf{Madurez de herramientas:} No todas las herramientas soportan todas las funcionalidades necesarias.
    \item \textbf{Personalización:} El código generado puede ser rígido y difícil de modificar.
    \item \textbf{Sobrecarga inicial:} Inversión de tiempo en modelos formales que puede no ser rentable en proyectos pequeños.
\end{itemize}

\subsection{Estado del Arte}

El campo de la transformación de modelos cuenta con más de 60 herramientas catalogadas \cite{kahani2019}. Los principales desafíos vigentes incluyen:

\begin{itemize}
    \item \textbf{Escalabilidad:} Manejo de modelos de gran tamaño con miles de elementos.
    \item \textbf{Interoperabilidad:} Intercambio de modelos entre diferentes herramientas mediante XMI.
    \item \textbf{Adopción industrial:} Integración con flujos de trabajo y herramientas existentes.
    \item \textbf{Mantenibilidad:} Evolución de modelos y transformaciones a lo largo del tiempo \cite{bucchiarone2020}.
\end{itemize}

% ============================================================================
% 4. JUSTIFICACIÓN DE LA HERRAMIENTA - Página 7
% ============================================================================
\newpage
\section{Justificación de la Elección de BOUML}

\subsection{Descripción de BOUML}

BOUML es una herramienta de modelado UML 2.0 de código abierto, desarrollada por Bruno Pagès y publicada bajo la Licencia Pública General de GNU (GPLv2) \cite{bouml}. Fue diseñada con un enfoque en el rendimiento y la eficiencia, compitiendo favorablemente con herramientas comerciales más pesadas.

\subsection{Características Principales}

\begin{itemize}
    \item \textbf{Código Abierto y Gratuito:} Accesible para entornos académicos y profesionales sin coste de licencia.
    \item \textbf{Multiplataforma:} Funciona en Windows, Linux, Solaris y Mac OS X.
    \item \textbf{Ultra-ligero:} Bajo consumo de memoria y alta velocidad, permitiendo trabajar con modelos de gran tamaño.
    \item \textbf{Soporte UML 2.0:} Cubre una amplia gama de diagramas UML.
    \item \textbf{Generación de Código:} Soporta C++, Java, Python, PHP, IDL y SQL.
    \item \textbf{Ingeniería Inversa:} Capacidad de recuperar modelos desde código existente.
    \item \textbf{Extensible:} Permite el desarrollo de plugins mediante API en C++ o Java.
    \item \textbf{Multi-usuario:} Soporte para trabajo colaborativo con control de versiones.
\end{itemize}

\subsection{Comparación con Otras Herramientas}

\begin{table}[H]
    \centering
    \caption{Comparación de herramientas MDD}
    \label{tab:comparacion}
    \begin{tabular}{|p{2.5cm}|p{2.5cm}|p{2.5cm}|p{2.5cm}|}
        \hline
        \textbf{Característica} & \textbf{BOUML} & \textbf{StarUML} & \textbf{Visual Paradigm} \\
        \hline
        Licencia & Gratuito (GPL) & Freemium & De pago \\
        Rendimiento & Muy Alto & Bajo & Medio \\
        Lenguajes Generados & C++, Java, Python, PHP, SQL & Java, C\#, Python & Java, C\#, PHP, Python \\
        Colaboración & No & No & Sí \\
        Extensibilidad & Sí & Sí & Sí \\
        Simulación & No & No & Sí \\
        Validación & No & No & Sí (OCL) \\
        \hline
    \end{tabular}
\end{table}

\subsection{Por qué BOUML para este Trabajo}

La selección de BOUML se justifica por las siguientes razones:

\begin{enumerate}
    \item \textbf{Accesibilidad:} Coste cero para todos los integrantes del equipo, sin barreras económicas.
    \item \textbf{Enfoque en MDD:} Flujo de trabajo claro que separa PIM de PSM, alineado con los conceptos teóricos.
    \item \textbf{Velocidad:} Permite iteraciones rápidas y regeneraciones ágiles, crucial para la demostración.
    \item \textbf{Soporte para C++:} Lenguaje nativo soportado por BOUML, alineado con los objetivos del proyecto.
    \item \textbf{Facilidad de demostración:} Interfaz clara y directa para la exposición en clase.
\end{enumerate}

% ============================================================================
% 5. DESCRIPCIÓN DEL PFC - Página 8
% ============================================================================
\newpage
\section{Descripción del PFC y Módulo Seleccionado}

\subsection{Proyecto Fin de Curso: SGCV-IA}

El Proyecto Fin de Curso consiste en el desarrollo de un \textbf{Sistema de Gestión Clínica Veterinaria con Inteligencia Artificial (SGCV-IA)}. El sistema está diseñado para optimizar y digitalizar los procesos administrativos y clínicos de una clínica veterinaria, integrando capacidades de inteligencia artificial para el apoyo diagnóstico.

\subsubsection{Objetivo General del PFC}

Desarrollar un sistema de software robusto, seguro y escalable que permita la gestión centralizada de pacientes (mascotas), clientes (dueños), historiales clínicos, citas, inventario y personal veterinario, facilitando la toma de decisiones y mejorando la experiencia de los usuarios.

\subsubsection{Alcance del Sistema}

El sistema abarcará múltiples módulos interconectados:

\begin{itemize}
    \item \textbf{Módulo de Gestión de Usuarios y Accesos (RBAC):} Administración de usuarios con control de acceso basado en roles, diferenciando entre Administradores, Veterinarios y Personal Administrativo.
    \item \textbf{Módulo de Gestión de Clientes y Mascotas:} Registro, actualización y consulta de información de dueños y sus mascotas.
    \item \textbf{Módulo de Gestión de Citas y Atenciones Clínicas:} Programación, modificación y cancelación de citas, así como el registro detallado de atenciones.
    \item \textbf{Módulo de Inteligencia Artificial:} Generación de sugerencias diagnósticas asistidas por IA, con validación obligatoria por parte del veterinario.
    \item \textbf{Módulo de Gestión de Inventario:} Control de stock de productos, alertas de vencimiento y umbrales mínimos.
    \item \textbf{Módulo de Facturación y Reportes:} Procesamiento de cobros, generación de facturas y reportes administrativos.
    \item \textbf{Módulo de Notificaciones:} Envío de recordatorios, alertas y comunicaciones a los dueños de mascotas.
\end{itemize}

\subsection{Módulo Seleccionado: Atenciones Clínicas}

Para la presente exposición, se ha seleccionado el \textbf{Módulo de Gestión de Citas Médicas (Atenciones Clínicas)}. Este módulo es crítico en cualquier sistema de salud veterinaria, ya que gestiona la interacción directa entre el paciente, el cliente y el servicio médico.

\subsubsection{Objetivo del Módulo}

Gestionar de manera eficiente y sin conflictos la agenda de los veterinarios, permitiendo a los clientes solicitar, reprogramar y cancelar citas para sus mascotas, y a los administradores controlar la disponibilidad horaria.

\subsubsection{Alcance del Módulo}

El módulo se encargará de:
\begin{itemize}
    \item Agendar nuevas atenciones clínicas verificando la disponibilidad del veterinario y el horario.
    \item Modificar los detalles de citas existentes (fecha, hora, motivo).
    \item Cancelar citas y liberar espacios en la agenda.
    \item Registrar atenciones completas con diagnóstico, tratamiento y medicamentos prescritos.
    \item Consultar historial de citas por mascota o cliente.
    \item Integrar diagnóstico asistido por IA durante la atención.
    \item Gestionar los estados de la atención a lo largo de su ciclo de vida.
\end{itemize}

\subsubsection{Actores del Módulo}

\begin{itemize}
    \item \textbf{Veterinario:} Consulta agenda, registra atenciones, valida sugerencias de IA.
    \item \textbf{Administrador/Secretario:} Gestiona citas, agendas, clientes y mascotas.
    \item \textbf{Dueño de Mascota (Cliente):} Solicita y consulta citas.
    \item \textbf{Sistema (Módulo IA):} Genera sugerencias diagnósticas y notificaciones.
\end{itemize}

\subsubsection{Funcionalidades}

\begin{enumerate}
    \item Registrar Atención Clínica
    \item Consultar Agenda
    \item Modificar Cita
    \item Cancelar Cita
    \item Ver Historial de Citas
    \item Integración con IA
    \item Gestión de Estados
    \item Reporte de Atenciones
\end{enumerate}

% ============================================================================
% 6. MODELO UML - Páginas 9-11
% ============================================================================
\newpage
\section{Modelo UML}

\subsection{Diagrama de Clases UML}

El diagrama de clases contiene más de 6 clases del dominio del PFC, con atributos tipados, operaciones con firma completa, visibilidad y cardinalidades correctas.

\begin{figure}[H]
    \centering
    \includegraphics[width=0.9\textwidth]{diagrama_clases.png}
    \caption{Diagrama de Clases UML del Módulo de Gestión de Atenciones Clínicas}
    \label{fig:diagrama_clases}
\end{figure}

\subsection{Clases Principales}

\begin{table}[H]
    \centering
    \caption{Clases del modelo UML}
    \label{tab:clases}
    \begin{tabular}{|p{3cm}|p{9cm}|}
        \hline
        \textbf{Clase} & \textbf{Descripción} \\
        \hline
        \texttt{Usuario} & Clase base abstracta para \texttt{Administrador} y \texttt{Veterinario}. Contiene atributos comunes como idUsuario, nombre, apellido, correo, contrasenia, rol y estado. \\
        \texttt{Administrador} & Personal con permisos de administración. Hereda de Usuario y añade el atributo cargo. Métodos: gestionarUsuarios() y generarReporte(). \\
        \texttt{Veterinario} & Profesional que atiende a las mascotas. Hereda de Usuario y añade especialidad y numeroLicencia. Métodos: consultarAgenda(), registrarAtencion() y validarSugerenciaIA(). \\
        \texttt{Cliente} & Dueño de la mascota. Atributos: idCliente, nombre, telefono, correo, direccion. Métodos: solicitarCita() y consultarHistorialMascotas(). \\
        \texttt{Mascota} & Paciente que recibe atención médica. Atributos: idMascota, nombre, especie, raza, sexo, fechaNacimiento, peso. Métodos: actualizarPeso() y consultarHistorialClinico(). \\
        \texttt{AtencionClinica} & Evento de consulta médica (clase central). Atributos: idAtencion, fecha, motivoConsulta, diagnostico, tratamiento, observaciones, estado. Métodos: iniciarAtencion(), solicitarDiagnosticoIA(), finalizarAtencion(), cancelarAtencion(), actualizarHistorial(). \\
        \texttt{HistorialClinico} & Registro médico completo de la mascota. Atributos: idHistorial, fechaCreacion, observaciones. Método: agregarRegistro(). \\
        \texttt{SugerenciaIA} & Sugerencia diagnóstica generada por IA. Atributos: idSugerencia, fechaGeneracion, diagnosticoSugerido, nivelConfianza, estado. Métodos: aceptar(), rechazar(), modificar(). \\
        \texttt{Producto} & Medicamentos e insumos. Atributos: idProducto, nombre, tipo, stock, fechaVencimiento, umbralMinimo. Métodos: descontarStock() y verificarVencimiento(). \\
        \texttt{Inventario} & Gestiona el inventario de productos. Atributos: idInventario, ubicacion, fechaActualizacion. Método: actualizarStock(). \\
        \texttt{Notificacion} & Notificaciones y alertas del sistema. Atributos: idNotificacion, mensaje, fecha, estado, tipo. Método: marcarComoVista(). \\
        \hline
    \end{tabular}
\end{table}

\subsection{Relaciones y Cardinalidades}

\begin{table}[H]
    \centering
    \caption{Relaciones del modelo UML}
    \label{tab:relaciones}
    \begin{tabular}{|p{4cm}|p{3cm}|p{4cm}|}
        \hline
        \textbf{Relación} & \textbf{Tipo} & \textbf{Cardinalidad} \\
        \hline
        Administrador → Usuario & Herencia & - \\
        Veterinario → Usuario & Herencia & - \\
        Cliente ↔ Mascota & Asociación & 1 ↔ 1..* \\
        Mascota ↔ AtencionClinica & Asociación & 1 ↔ 0..* \\
        Veterinario ↔ AtencionClinica & Asociación & 1 ↔ 0..* \\
        Mascota → HistorialClinico & Composición & 1 → 1 \\
        Inventario → Producto & Agregación & 1 → 0..* \\
        Administrador ↔ Inventario & Asociación & 1 ↔ 1 \\
        AtencionClinica ↔ SugerenciaIA & Asociación & 1 ↔ 0..1 \\
        Veterinario ↔ SugerenciaIA & Asociación & 1 ↔ 0..* \\
        Cliente ↔ HistorialClinico & Asociación & 1 ↔ 0..* \\
        Inventario ↔ Notificacion & Asociación & 1 ↔ 0..* \\
        \hline
    \end{tabular}
\end{table}

\subsection{Diagramas Complementarios}

\subsubsection{Diagrama de Casos de Uso}

\begin{figure}[H]
    \centering
    \includegraphics[width=0.8\textwidth]{diagrama_casos_uso.png}
    \caption{Diagrama de Casos de Uso del Módulo de Atenciones Clínicas}
    \label{fig:diagrama_casos_uso}
\end{figure}

\subsubsection{Diagrama de Máquina de Estados}

\begin{figure}[H]
    \centering
    \includegraphics[width=0.9\textwidth]{diagrama_estados.png}
    \caption{Diagrama de Máquina de Estados de la entidad AtencionClinica}
    \label{fig:diagrama_estados}
\end{figure}

% ============================================================================
% 7. CONFIGURACIÓN DEL GENERADOR - Página 12
% ============================================================================
\newpage
\section{Configuración del Generador}

\subsection{Configuración de BOUML para C++}

La generación de código en BOUML se configura a través del menú \texttt{Project > Edit Generation Settings}. En la ventana de configuración, se debe seleccionar el lenguaje C++ en la pestaña correspondiente.

\subsubsection{Lenguajes Soportados por BOUML}

Según la captura de pantalla de la herramienta, BOUML soporta los siguientes lenguajes:

\begin{itemize}
    \item \textbf{C++} - Gestión de declaraciones/definiciones por defecto
    \item Java - Gestión y definición por defecto
    \item PHP - Gestión y definición por defecto
    \item Python - Gestión y definición por defecto
    \item IDL - Gestión de declaraciones por defecto
    \item MySQL - Gestión y definición por defecto
\end{itemize}

\textbf{Nota:} C\# no está disponible en BOUML, por lo que se ha seleccionado \textbf{C++} como lenguaje objetivo.

\subsection{Parámetros de Configuración}

\begin{table}[H]
    \centering
    \caption{Configuración del generador en BOUML para C++}
    \label{tab:configuracion}
    \begin{tabular}{|p{3cm}|p{9cm}|}
        \hline
        \textbf{Parámetro} & \textbf{Configuración} \\
        \hline
        Default target language & C++ \\
        Default source directory & ./CodigoGenerado \\
        Verbose code generation & Activado \\
        Preserve operations's body & Activado \\
        Add operation profile on body edition & Activado \\
        Política de regeneración & Actualización incremental \\
        \hline
    \end{tabular}
\end{table}

\subsection{Configuración de Artefactos}

Se creó una Deployment View llamada \texttt{DeploySGCVIA} y se asoció a la Class View \texttt{VistaSGCVIA}. Cada clase tiene un artefacto asociado que genera un archivo \texttt{.h} (cabecera) y \texttt{.cpp} (implementación). Este paso es fundamental para que BOUML sepa qué código debe generar y dónde ubicarlo.

\begin{figure}[H]
    \centering
    \includegraphics[width=0.7\textwidth]{configuracion_generador.png}
    \caption{Configuración de la Generación de Código en BOUML}
    \label{fig:configuracion_generador}
\end{figure}

% ============================================================================
% 8. GENERACIÓN Y VERIFICACIÓN - Páginas 13-14
% ============================================================================
\newpage
\section{Generación y Verificación del Código}

\subsection{Proceso de Generación en C++}

La generación se ejecuta desde la vista de despliegue seleccionando \texttt{Generate > C++}. BOUML procesa el modelo y genera los archivos \texttt{.h} (declaraciones) y \texttt{.cpp} (definiciones) correspondientes.

\subsubsection{Flujo de Generación}

\begin{enumerate}
    \item \textbf{Análisis del modelo:} BOUML recorre todas las clases, atributos, métodos y relaciones definidas en el diagrama de clases.
    \item \textbf{Aplicación de configuración:} Se aplican las reglas de generación configuradas en "Edit Generation Settings".
    \item \textbf{Generación de archivos:} Se escriben los archivos .h y .cpp en el directorio de salida.
    \item \textbf{Validación:} Se verifica que el código generado sea sintácticamente correcto.
\end{enumerate}

\begin{figure}[H]
    \centering
    \includegraphics[width=0.7\textwidth]{proceso_generacion.png}
    \caption{Proceso de Generación de Código en BOUML}
    \label{fig:proceso_generacion}
\end{figure}

\subsection{Estructura de Archivos Generados en C++}

Para cada clase, BOUML genera dos archivos:

\begin{itemize}
    \item \textbf{Archivo .h (Header):} Contiene la declaración de la clase, atributos, métodos y relaciones.
    \item \textbf{Archivo .cpp (Implementation):} Contiene la implementación de los métodos (con cuerpos vacíos por defecto).
\end{itemize}

\subsection{Verificación del Código Generado}

El código generado fue compilado en un entorno C++ (Visual Studio, GCC o similar) sin errores. La siguiente tabla muestra la correspondencia entre los elementos del modelo y los artefactos generados:

\begin{table}[H]
    \centering
    \caption{Correspondencia modelo-código en C++}
    \label{tab:correspondencia}
    \begin{tabular}{|p{3cm}|p{3cm}|p{6cm}|}
        \hline
        \textbf{Clase UML} & \textbf{Archivo Generado} & \textbf{Contenido} \\
        \hline
        \texttt{Usuario} & \texttt{Usuario.h / .cpp} & Clase abstracta con atributos y métodos \\
        \texttt{Administrador} & \texttt{Administrador.h / .cpp} & Hereda de Usuario, atributo \texttt{cargo} \\
        \texttt{Veterinario} & \texttt{Veterinario.h / .cpp} & Hereda de Usuario, atributos \texttt{especialidad}, \texttt{numeroLicencia} \\
        \texttt{Cliente} & \texttt{Cliente.h / .cpp} & Atributos \texttt{nombre}, \texttt{telefono}, \texttt{correo}, \texttt{direccion} \\
        \texttt{Mascota} & \texttt{Mascota.h / .cpp} & Atributos \texttt{nombre}, \texttt{especie}, \texttt{raza}, \texttt{peso} \\
        \texttt{AtencionClinica} & \texttt{AtencionClinica.h / .cpp} & Atributos \texttt{fecha}, \texttt{motivoConsulta}, \texttt{diagnostico}, \texttt{estado} \\
        \texttt{HistorialClinico} & \texttt{HistorialClinico.h / .cpp} & Atributos \texttt{fechaCreacion}, \texttt{observaciones} \\
        \texttt{SugerenciaIA} & \texttt{SugerenciaIA.h / .cpp} & Atributos \texttt{diagnosticoSugerido}, \texttt{nivelConfianza}, \texttt{estado} \\
        \hline
    \end{tabular}
\end{table}

\subsection{Limitaciones Detectadas}

\begin{itemize}
    \item Los cuerpos de los métodos se generan vacíos (con comentario para implementar)
    \item No se genera automáticamente la lógica de negocio
    \item Se requiere implementar manualmente la lógica de validación y persistencia
    \item La gestión de colecciones (List, Vector) debe ser configurada manualmente en las plantillas de C++
    \item Las relaciones de composición y agregación no se traducen automáticamente a punteros inteligentes
\end{itemize}

% ============================================================================
% 9. ROUNDTRIP - Página 15
% ============================================================================
\newpage
\section{Roundtrip Engineering}

\subsection{Demostración Práctica en C++}

Se ejecutó un cambio significativo en el modelo: la adición del atributo \texttt{peso} a la clase \texttt{Mascota}.

\subsubsection{Antes del Cambio}

\begin{figure}[H]
    \centering
    \includegraphics[width=0.5\textwidth]{modelo_inicial.png}
    \caption{Modelo Inicial de la Clase \texttt{Mascota}}
    \label{fig:modelo_inicial}
\end{figure}

\subsubsection{Pasos del Roundtrip}

\begin{enumerate}
    \item \textbf{Modificación del modelo:} Agregar atributo \texttt{peso: float} a la clase \texttt{Mascota} en BOUML.
    \item \textbf{Regeneración del código:} Ejecutar \texttt{Generate > C++} en la Deployment View.
    \item \textbf{Verificación del cambio:} Los archivos \texttt{Mascota.h} y \texttt{Mascota.cpp} se actualizan automáticamente.
\end{enumerate}

\subsubsection{Después del Cambio}

Se agregó el atributo \texttt{peso} al modelo y se regeneró el código. Los archivos \texttt{Mascota.h} y \texttt{Mascota.cpp} se actualizaron automáticamente con la nueva declaración e implementación.

\begin{figure}[H]
    \centering
    \includegraphics[width=0.5\textwidth]{codigo_actualizado.png}
    \caption{Código Actualizado de \texttt{Mascota.cpp}}
    \label{fig:codigo_actualizado}
\end{figure}

\subsection{Traza del Cambio}

El cambio en el modelo se reflejó en el código sin perder el trabajo manual implementado en los métodos. BOUML actualizó los archivos añadiendo:

\begin{enumerate}
    \item El nuevo atributo en la sección privada de la clase.
    \item Los métodos getter y setter correspondientes.
    \item Las declaraciones necesarias en el archivo de cabecera.
\end{enumerate}

\subsection{Ventajas del Roundtrip con BOUML}

\begin{itemize}
    \item \textbf{Preservación del código manual:} BOUML respeta el código escrito manualmente en los métodos.
    \item \textbf{Actualización incremental:} Solo se modifican los elementos cambiados, no todo el archivo.
    \item \textbf{Documentación viva:} El modelo y el código siempre están sincronizados.
\end{itemize}

% ============================================================================
% 10. TRABAJO DEL EQUIPO - Página 16
% ============================================================================
\newpage
\section{Distribución del Trabajo por Integrante}

\begin{table}[H]
    \centering
    \caption{Distribución del trabajo por integrante}
    \label{tab:distribucion}
    \begin{tabular}{|p{3cm}|p{10cm}|}
        \hline
        \textbf{Integrante} & \textbf{Tareas} \\
        \hline
        \textbf{Robison Jenapierrel} & Marco teórico, referencias académicas, repositorio, guion de exposición (parte 1) \\
        \hline
        \textbf{Arteaga Danela} & Introducción, descripción del PFC, conclusiones, anexos, referencias IEEE, diapositivas, guion (parte 4) \\
        \hline
        \textbf{Herrera Thais} & Instalación BOUML, diagrama de clases UML, manual de BOUML, capturas, justificación de herramienta, guion (parte 2) \\
        \hline
        \textbf{Marcillo Jeanpool} & Generación de código en C++, verificación en Visual Studio, Roundtrip Engineering, tabla de verificación, guion (parte 3) \\
        \hline
    \end{tabular}
\end{table}

\textbf{Commits en GitHub:} Cada integrante realizó commits diferenciados en el repositorio, con identidad Git verificable.

\begin{figure}[H]
    \centering
    \includegraphics[width=0.8\textwidth]{contribuacion_commits.png}
    \caption{Captura de GitHub Insights → Contributors}
    \label{fig:contributors}
\end{figure}


% ============================================================================
% 11. CONCLUSIONES - Página 17
% ============================================================================
\newpage
\section{Conclusiones}

La realización de este trabajo de exposición sobre Model-Driven Development (MDD) con BOUML ha permitido consolidar los conceptos teóricos de la asignatura de Ingeniería de Requisitos a través de una aplicación práctica.

\textbf{Principales Aprendizajes:}

\begin{enumerate}
    \item \textbf{Valor del MDD:} La separación de la lógica de negocio (PIM) de los detalles de implementación (PSM) a través de modelos UML facilita la portabilidad y el mantenimiento del software \cite{schmidt2006, selic2003}. La generación automática de código reduce errores y acelera el desarrollo, permitiendo a los desarrolladores centrarse en la lógica de negocio en lugar de en código repetitivo.
    
    \item \textbf{BOUML como Herramienta Efectiva:} A pesar de su interfaz austera, BOUML se ha mostrado como una herramienta poderosa, eficiente y ágil para el modelado UML y la generación de código en C++. Su velocidad y bajo consumo de recursos permiten iterar rápidamente, lo que es ideal para un entorno académico y de demostración.
    
    \item \textbf{Importancia del Roundtrip:} La capacidad de mantener sincronizados el modelo y el código es fundamental para que el modelo no se convierta en una pieza de documentación obsoleta \cite{pohl2025}. El Roundtrip Engineering convierte al modelo en un "contrato vivo" que guía la evolución del sistema, evitando la "deriva modelo-código" y manteniendo la trazabilidad.
    
    \item \textbf{Aplicación en un Contexto Real:} El uso del módulo de Gestión de Atenciones Clínicas del SGCV-IA ha demostrado la aplicabilidad de MDD a un dominio con una lógica de negocio bien definida. La integración de conceptos como el modelo de datos (14 entidades), el diagrama de casos de uso y la máquina de estados ha evidenciado que los conceptos aprendidos en el aula trascienden los ejemplos académicos.
    
    \item \textbf{Desafíos del MDD:} La curva de aprendizaje inicial y la necesidad de invertir tiempo en modelos formales son barreras que deben considerarse. Sin embargo, los beneficios en productividad, calidad y mantenibilidad a largo plazo justifican su adopción, especialmente en sistemas complejos.
    
    \item \textbf{Limitación de Lenguajes:} BOUML no soporta C\#, por lo que se utilizó C++ como lenguaje objetivo, demostrando la flexibilidad de la herramienta para trabajar con múltiples lenguajes, pero también evidenciando la necesidad de verificar la compatibilidad antes de seleccionar la herramienta.
\end{enumerate}

\subsection{Contribución al PFC}

Este trabajo sienta las bases para la integración del enfoque MDD en el desarrollo del SGCV-IA. La generación automática de código a partir del modelo UML permitirá mantener la consistencia entre el diseño y la implementación, acelerar el desarrollo de nuevos módulos, facilitar el mantenimiento y la evolución del sistema, y reducir la introducción de errores humanos.

\subsection{Recomendaciones}

\begin{enumerate}
    \item Evaluar herramientas alternativas que soporten C\# para futuros proyectos.
    \item Profundizar en transformaciones M2M utilizando QVT para transformaciones más complejas.
    \item Implementar pruebas automatizadas para validar el código generado.
    \item Personalizar las plantillas de generación para adaptarlas a las necesidades del proyecto.
\end{enumerate}

% ============================================================================
% 12. REFERENCIAS BIBLIOGRÁFICAS
% ============================================================================
\newpage
\section{Referencias}

\begin{thebibliography}{99}

\bibitem{schmidt2006}
D. C. Schmidt, ``Guest editor's introduction: Model-driven engineering,'' \emph{Computer}, vol.~39, no.~2, pp.~25--31, Feb. 2006, doi: 10.1109/MC.2006.58.

\bibitem{selic2003}
B. Selic, ``The pragmatics of model-driven development,'' \emph{IEEE Software}, vol.~20, no.~5, pp.~19--25, Sep. 2003, doi: 10.1109/MS.2003.1231146.

\bibitem{pohl2025}
K. Pohl, \emph{Requirements Engineering: Fundamentals, Principles, and Techniques}, 2nd ed. Berlin: Springer, 2025.

\bibitem{omg2014}
Object Management Group, ``Model Driven Architecture (MDA) Guide,'' OMG, Tech. Rep. ormsc/14-06-01, Rev. 2.0, 2014.

\bibitem{omg2017}
Object Management Group, ``OMG Unified Modeling Language (OMG UML),'' OMG, Tech. Rep. formal/17-12-05, Version 2.5.1, 2017.

\bibitem{omg2016}
Object Management Group, ``Meta Object Facility (MOF) 2.0 Query/View/Transformation Specification,'' OMG, Tech. Rep. formal/16-06-03, Version 1.3, 2016.

\bibitem{omg2008}
Object Management Group, ``MOF Model To Text Transformation Language (MOFM2T),'' OMG, Tech. Rep. formal/2008-01-16, Version 1.0, 2008.

\bibitem{ieee29148}
ISO/IEC/IEEE, ``Systems and software engineering --- Life cycle processes --- Requirements engineering,'' ISO/IEC/IEEE 29148:2018, 2018.

\bibitem{bouml}
B. Pagès, \emph{BOUML: A free UML 2 tool box}, 2024. [Online]. Available: \url{http://bouml.free.fr/}. Accessed: Jun. 2024.

\bibitem{bucchiarone2020}
A. Bucchiarone, J. Cabot, R. F. Paige, and A. Pierantonio, ``Grand challenges in model-driven engineering: an analysis of the state of the research,'' \emph{Software and Systems Modeling}, vol.~19, no.~1, pp.~5--13, 2020, doi: 10.1007/s10270-019-00773-6.

\bibitem{brambilla2017}
M. Brambilla, J. Cabot, and M. Wimmer, \emph{Model-Driven Software Engineering in Practice}, 2nd ed., Synthesis Lectures on Software Engineering. Morgan \& Claypool Publishers, 2017, doi: 10.2200/S00751ED2V01Y201701SWE001.

\bibitem{kahani2019}
N. Kahani, M. Bagherzadeh, J. R. Cordy, J. Dingel, and D. Varro, ``Survey and classification of model transformation tools,'' \emph{Software and Systems Modeling}, vol.~18, no.~4, pp.~2361--2397, 2019, doi: 10.1007/s10270-018-0665-6.

\bibitem{swebok2024}
IEEE Computer Society, \emph{Guide to the Software Engineering Body of Knowledge (SWEBOK)}, v4.0, 2024.

\end{thebibliography}

% ============================================================================
% 13. ANEXOS (NO CUENTA PARA EL LÍMITE DE 20 PÁGINAS)
% ============================================================================
\newpage
\section{Anexos}

\subsection{Anexo A: Código Fuente Generado en C++}

\subsubsection{Archivo de Cabecera (Mascota.h)}

\begin{lstlisting}[language=C++, caption=Código generado para la clase Mascota - Mascota.h]
//  Generated by BOUML, version: 6.7.9
//  Generated from "ModeloAtenciones", on: 2024-07-18

#ifndef MASCOTA_H
#define MASCOTA_H

#include <string>
#include "HistorialClinico.h"

class Mascota
{
private:
    std::string especie;
    std::string nombre;
    float peso;
    std::string raza;
    std::string sexo;
    std::string fechaNacimiento;

public:
    Mascota();
    ~Mascota();

    // Getters
    std::string getEspecie() const;
    std::string getNombre() const;
    float getPeso() const;
    std::string getRaza() const;
    std::string getSexo() const;
    std::string getFechaNacimiento() const;

    // Setters
    void setEspecie(const std::string& value);
    void setNombre(const std::string& value);
    void setPeso(float value);
    void setRaza(const std::string& value);
    void setSexo(const std::string& value);
    void setFechaNacimiento(const std::string& value);

    // Métodos
    void actualizarPeso(float nuevoPeso);
    HistorialClinico* consultarHistorialClinico();
};

#endif // MASCOTA_H
\end{lstlisting}

\subsubsection{Archivo de Implementación (Mascota.cpp)}

\begin{lstlisting}[language=C++, caption=Código generado para la clase Mascota - Mascota.cpp]
//  Generated by BOUML, version: 6.7.9
//  Generated from "ModeloAtenciones", on: 2024-07-18

#include "Mascota.h"
#include "HistorialClinico.h"

Mascota::Mascota()
{
    // Constructor vacío
}

Mascota::~Mascota()
{
    // Destructor
}

// Getters
std::string Mascota::getEspecie() const
{
    return this->especie;
}

std::string Mascota::getNombre() const
{
    return this->nombre;
}

float Mascota::getPeso() const
{
    return this->peso;
}

// Setters
void Mascota::setEspecie(const std::string& value)
{
    this->especie = value;
}

void Mascota::setNombre(const std::string& value)
{
    this->nombre = value;
}

void Mascota::setPeso(float value)
{
    this->peso = value;
}

// Métodos
void Mascota::actualizarPeso(float nuevoPeso)
{
    // TODO: Implementar lógica de actualización de peso
    this->peso = nuevoPeso;
}

HistorialClinico* Mascota::consultarHistorialClinico()
{
    // TODO: Implementar lógica de consulta de historial
    return nullptr;
}
\end{lstlisting}

\subsection{Anexo B: Estructura del Repositorio}

\begin{figure}[H]
    \centering
    \includegraphics[width=0.9\textwidth]{estructura_repositorio.png}
    \caption{Estructura del Repositorio en GitHub}
    \label{fig:estructura_repositorio}
\end{figure}

\subsection{Anexo C: Lenguajes Soportados por BOUML}

\begin{table}[H]
    \centering
    \caption{Lenguajes soportados por BOUML según captura de pantalla}
    \label{tab:lenguajes}
    \begin{tabular}{|p{4cm}|p{4cm}|p{4cm}|}
        \hline
        \textbf{Lenguaje} & \textbf{Soporte} & \textbf{Características} \\
        \hline
        C++ & Completo & Gestión de declaraciones/definiciones \\
        Java & Completo & Gestión y definición por defecto \\
        PHP & Completo & Gestión y definición por defecto \\
        Python & Completo & Gestión y definición por defecto \\
        IDL & Parcial & Gestión de declaraciones por defecto \\
        MySQL & Parcial & Gestión y definición por defecto \\
        \hline
    \end{tabular}
\end{table}


\subsection{Anexo D: Reunión del trabajo realizado}

Durante la reunión se revisaron los avances obtenidos en el desarrollo del proyecto, verificando las actividades realizadas por cada integrante y el cumplimiento de las tareas asignadas. Además, se comprobó la participación de los miembros mediante los commits registrados en el repositorio de GitHub, donde cada contribución cuenta con una identidad Git verificable.

\begin{figure}[H]
    \centering
    \includegraphics[width=0.8\textwidth]{contributors.png}
    \caption{Captura de GitHub Insights → Contributors}
    \label{fig:contributors}
\end{figure}
\end{document}
