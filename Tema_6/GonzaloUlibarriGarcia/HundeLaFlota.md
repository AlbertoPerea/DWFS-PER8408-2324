
Juego (games): Identifica un juego determinado.
Usuarios (users): Identifica un usuario dado.
Barcos (ships): Identifica a los barcos de un juego.
Disparos (shots): Identifica a los disparos que se han realizado en las diferentes casillas.


| Método HTTP | URI                                           | Query Params                | Request Body                                                        | Response Body                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Códigos HTTP de respuesta                                     |
|-------------|-----------------------------------------------|-----------------------------|---------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| POST        | /games                                        | N/A                         | N/A                                                                 | `{"gameID":1, "player1ID":1, "player2ID":2 } `                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | 201 Created<br/>400 Bad Request<br/>500 Internal Server Error |
| DELETE      | /games/{gameID}                               | gameID                      | N/A                                                                 | N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | 200 OK<br/>400 Bad Request<br/>500 Internal Server Error      |
| PATCH       | /games/{gameID}                               | gameID                      | `{"winner": "Gonzalo"}`                                             | N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | 200 OK<br/>404 Not Found<br/>500 Internal Server Error        |
| GET         | /games/{gameID}                               | gameID, playerID            | N/A                                                                 | `{ "game" : { "winner": "none", player1":{"playerID":1,"ships":[{"name":"Aircraft Carrier","position":["A1","A2","A3","A4","A5"]},{"name":"Battleship1","position":["B1","B2","B3","B4"]},{"name":"Battleship2","position":["C1","C2","C3","C4"]},{"name":"Destroyer1","position":["D1","D2","D3"]},{"name":"Destroyer2","position":["E1","E2","E3"]},{"name":"Destroyer3","position":["F1","F2","F3"]},{"name":"Submarine1","position":["G1","G2","G3"]},{"name":"Submarine2","position":["H1","H2","H3"]},{"name":"Submarine3","position":["I1","I2","I3"]},{"name":"Submarine4","position":["J1","J2","J3"]}],"shots":["A6","B5"]},"player2":{"playerID":2,"ships":[{"name":"Aircraft Carrier","position":["K1","K2","K3","K4","K5"]},{"name":"Battleship1","position":["A1","A2","A3","A4"]},{"name":"Battleship2","position":["B1","B2","B3","B4"]},{"name":"Destroyer1","position":["C1","C2","C3"]},{"name":"Destroyer2","position":["D1","D2","D3"]},{"name":"Destroyer3","position":["E1","E2","E3"]},{"name":"Submarine1","position":["F1","F2","F3"]},{"name":"Submarine2","position":["G1","G2","G3"]},{"name":"Submarine3","position":["H1","H2","H3"]},{"name":"Submarine4","position":["I1","I2","I3"]}],"shots":["C4","D5"]}}}` | 200 OK<br/>404 Not Found<br/>500 Internal Server Error        |
| PATCH       | /games/{gameID}/{playerID}/ships              | gameID, playerID            | `{"name":"Aircraft Carrier","position":["A1","A2","A3","A4","A5"]}` | N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | 200 OK<br/>404 Not Found<br/>500 Internal Server Error        |
| DELETE      | /games/{gameID}/{playerID}/ships              | gameID, playerID            | `{"name":"Aircraft Carrier","position":["A1","A2","A3","A4","A5"]}` | N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | 200 OK<br/>400 Bad Request<br/>500 Internal Server Error      |
| GET         | /games/{gameID}/{playerID}/ships              | gameID, playerID            | N/A                                                                 | `[{"name":"Aircraft Carrier","position":["A1","A2","A3","A4","A5"]},{"name":"Battleship1","position":["B1","B2","B3","B4"]},{"name":"Battleship2","position":["C1","C2","C3","C4"]},{"name":"Destroyer1","position":["D1","D2","D3"]},{"name":"Destroyer2","position":["E1","E2","E3"]},{"name":"Destroyer3","position":["F1","F2","F3"]},{"name":"Submarine1","position":["G1","G2","G3"]},{"name":"Submarine2","position":["H1","H2","H3"]},{"name":"Submarine3","position":["I1","I2","I3"]},{"name":"Submarine4","position":["J1","J2","J3"]}] `                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | 200 OK<br/>404 Not Found<br/>500 Internal Server Error        |
| POST        | /games/{gameID}/{player1ID}/shots/{player2ID} | gameID, player1ID,player2ID | `{"shot": "F8"}`                                                    | `{"status": "hit"}`, `{"status": "fail"}`  or `{"status": "sunken"}`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | 200 OK<br/>404 Not Found<br/>500 Internal Server Error        |
| POST        | /user                                         | N/A                         | `{ "name": "Gonzalo"}`                                              | `{"playerID": 1}`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | 201 Created<br/>400 Bad Request<br/>500 Internal Server Error |
| GET         | /user/{playerID}                              | playerID                    | N/A                                                                 | `{ "name": "Gonzalo"}`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | 200 OK<br/>404 Not Found<br/>500 Internal Server Error        |
| DELETE      | /user/{playerID}                              | playerID                    | N/A                                                                 | N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | 200 OK<br/>404 Not Found<br/>500 Internal Server Error        |