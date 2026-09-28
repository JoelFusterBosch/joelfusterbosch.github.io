Aquests apunts estan en el laboratori del mòdul 3, aquest no cobreix com fer completament el laboratori, sino de com utilitzar les eines de AWS

## Permisos de sols escritura (Only-Writing) en un EC2

Per a entrar a modificar el EC2 per a que els qui accedisquen sols tinguen permisos de lectura, el que has de fer és anar a la pàgina del administrador de AWS i seguir la següent ruta de opcions:

IAM > Políticas > `Nom del EC2`

I en el apartat de permisos pots posar una  estructura JSON pareguda com aquesta:

```json
"Statement": [
    {
        "Effect": "Allow",
        "Action": [
            "ec2:Describe",
            "ec2:GetSecurityGroupsForVpc"
        ],
        "Resource": "*"
    }
]
...
```

## Permisos de sols escritura (Only-Writing) en un S3

Seguim la mateixa ruta que haviem fet en el EC2, però en lloc de dirigirmo'n a un EC2, ens dirigirem a un S3 o siga: 

IAM > Políticas > `Nom del S3`

I en el apartat de permisos pots posar una  estructura JSON pareguda com aquesta:

```json
"Statement": [
    {
        "Effect": "Allow",
        "Action": [
            "s3:Get",
            "s3:List",
            "s3:Describe",
            "s3-object-lambda:Get",
            "s3-object-describe:List"
        ],
        "Resource": "*"
    }
]
...
```

## Modificar permisos d'un EC2 de administrador

Ara per a modificar els permisos d'un EC2 fem el mateix d'abans d'entrar en IAM, però en este cas no entrem a Politiques, hem d'entrar a Grups de persones i d'allí EC2-Admin i li apretem a `Editar la política` i coloques els canvis on diu `Editor de políticas`:

```json
"Statement": [
    {
        "Condition": {
            "ForAllValues:StringLikeIfExists": {
                "ec2:InstanceType": [
                    "*.nano",
                    "*.micro"
                ]
            }
        },

        "Action": [
            "ec2:Describe",
            "ec2:StartInstances",
            "ec2:StopInstances"
        ],

        "Resource": "*",

        "Effect": "Allow"
    }
]
```

### Provar els usuareis i els permisos

Per últim es proven els usuaris si els permisos s'han aplicat correctament:

