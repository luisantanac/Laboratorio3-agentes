# Laboratorio3-agentes
Inteligencia Artificial para la Gestión Territorial - Laboratorio 3

turtles-own [muertesubita energia edad muerte]
to configurar
  clear-all
  create-turtles 20
  ask turtles
  [
  setxy random-xcor random-ycor
  set energia 10;
  set edad 0;
  set muertesubita false;
  set muerte 0;
  ]
  ask patches [
  set pcolor pink
  ]

end

to programa
mover
comer
muertesubi
cementerio

end

to mover
  ask turtles [
    set heading heading + random 100
    forward 1
    set edad random 4 - 0
    set energia energia - 1
  ]
end

to comer
  ask turtles [
    if (pcolor = pink) and (edad = 1)[
      set pcolor black
      set energia random 3 - 0 - 1
    ]
  ]
end

to muertesubi
  ask turtles [
    set muerte random 10 - 0
    if muerte = 7 [
        set muertesubita true
    ]

  ]
end

to cementerio
  ask turtles [
    if energia <= 0
    [die]
    if edad > 120
    [die]
    if muertesubita = true
    [die]
  ]
end

