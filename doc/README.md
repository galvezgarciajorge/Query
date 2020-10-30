
***Los que tienen qty = 100 y status = "A"
Hecho con un and implícito***

< db.querysbd.find({ qty:100, status: "A"}).pretty()
{
        "_id" : ObjectId("5f9b6c36da1a8ebf91df4751"),
        "item" : "macbookprob",
        "qty" : 100,
        "size" : {
                "h" : 1.62,
                "w" : 35.79,
                "oum" : "cm"
        },
        "status" : "A"
}
>
***Los que tienen qty > 200 y < 80
No funciona con el mismo campo el and implícito***

< db.querysbd.find({$and: [ {qty: {$lt: 200}}, {qty: {$gt: 80}}]}).pretty()
{
        "_id" : ObjectId("5f9b6c36da1a8ebf91df4751"),
        "item" : "macbookprob",
        "qty" : 100,
        "size" : {
                "h" : 1.62,
                "w" : 35.79,
                "oum" : "cm"
        },
        "status" : "A"
}
{
        "_id" : ObjectId("5f9b6c36da1a8ebf91df4753"),
        "item" : "ipadpro",
        "qty" : 150,
        "size" : {
                "h" : 12.9,
                "oum" : "in"
        },
        "status" : "B"
}
{
        "_id" : ObjectId("5f9b6f8cda1a8ebf91df4756"),
        "item" : "macbookprob",
        "qty" : 100,
        "size" : {
                "h" : 1.62,
                "w" : 35.79,
                "oum" : "cm"
        },
        "status" : "A"
}
{
        "_id" : ObjectId("5f9b6f8cda1a8ebf91df4758"),
        "item" : "ipadpro",
        "qty" : 150,
        "size" : {
                "h" : 12.9,
                "oum" : "in"
        },
        "status" : "B"
}
<

***Los que tienen qty > 200 y < 80
Con and implícito pero sin repetir en nombre del campo qty***

< db.querysbd.find({qty: {$lt: 200, $gt: 80}}).pretty() 
{
        "_id" : ObjectId("5f9b6c36da1a8ebf91df4751"),  
        "item" : "macbookprob",
        "qty" : 100,
        "size" : {
                "h" : 1.62,
                "w" : 35.79,
                "oum" : "cm"
        },
        "status" : "A"
}
{
        "_id" : ObjectId("5f9b6c36da1a8ebf91df4753"),
        "item" : "ipadpro",
        "qty" : 150,
        "size" : {
                "h" : 12.9,
                "oum" : "in"
        },
        "status" : "B"
}
{
        "_id" : ObjectId("5f9b6f8cda1a8ebf91df4756"),
        "item" : "macbookprob",
        "qty" : 100,
        "size" : {
                "h" : 1.62,
                "w" : 35.79,
                "oum" : "cm"
        },
        "status" : "A"
}
{
        "_id" : ObjectId("5f9b6f8cda1a8ebf91df4758"),
        "item" : "ipadpro",
        "qty" : 150,
        "size" : {
                "h" : 12.9,
                "oum" : "in"
        },
        "status" : "B"
}
<

