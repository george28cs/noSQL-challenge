# Reto de BD noSQL (MongoDB)

## Estructura del documento.
{
    "_id": {
        "$oid": "5f85c16f1658ce2d2da39e34"
    },
    "nombre_alumno": "Alumno 1",
    "edad": 16,
    "examenes": [{
        "_id": {
            "$oid": "5f85c3011658ce2d2da39e36"
        },
        "nombre": "estadística",
        "calificacion": 85
    }, {
        "_id": {
            "$oid": "5f85c4ad1658ce2d2da39e3f"
        },
        "nombre": "conjuntos",
        "calificacion": 90
    }, {
        "_id": {
            "$oid": "5f85c4cf1658ce2d2da39e40"
        },
        "nombre": "ecuaciones",
        "calificacion": 95
    }]
}

## Query para calcular promedio

db.math_competition.aggregate([
       { 
           "$addFields": { 
               "promedio": {
                   "$divide": [
                       { // expression returns total
                           "$reduce": {
                               "input": "$examenes",
                               "initialValue": 0,
                               "in": { "$add": ["$$value", "$$this.calificacion"] }
                           }
                       },
                       { // expression returns ratings count
                           "$cond": [
                               { "$ne": [ { "$size": "$examenes" }, 0 ] },
                               { "$size": "$examenes" }, 
                               1
                           ]
                       }
                   ]
               }
           }
       }
])
