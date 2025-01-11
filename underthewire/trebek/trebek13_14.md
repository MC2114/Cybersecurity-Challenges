## Level Goal
The password for trebek14 is the last name of the user who has an encoded PowerShell command in their City property PLUS the name of the file on the desktop.

## Solution
Use <code>Get-ADUsert</code> (finally, something else...) and look at all of the available users on the machine. It is a very long list, but thankfully, the target we are looking for is pretty obvious since they are the only one with a non-null City value. And the <code>a...</code> looks very suspicious...
```powershell
PS C:\users\trebek13\desktop> ls


    Directory: C:\users\trebek13\desktop


Mode                LastWriteTime         Length Name                          
----                -------------         ------ ----                          
-a----        8/30/2018  10:49 AM              0 3003

PS C:\users\trebek13\desktop> Get-ADUser -Filter * -Properties Name, City | sele
ct Name, City                                                                   
                                                                                
Name                      City                                                  
----                      ----                                                  
Administrator                                                                   
Guest                                                                           
DefaultAccount                                                                  
krbtgt                                                                          
century1                                                                        
century2                                                                        
century3                                                                        
century4                                                                        
century5                                                                        
century6                                                                        
century7                                                                        
century8                                                                        
century9                                                                        
century10                                                                       
century11                                                                       
century12                                                                       
century13                                                                       
century14                                                                       
century15                                                                       
trebek1                                                                         
trebek2                                                                         
trebek3                                                                         
trebek4                                                                         
trebek5                                                                         
trebek6                                                                         
trebek7                                                                         
trebek8                                                                         
trebek9                                                                         
trebek10                                                                        
trebek11                                                                        
trebek12                                                                        
trebek13                                                                        
trebek14                                                                        
trebek15                                                                        
cyborg1                                                                         
cyborg2                                                                         
cyborg3                                                                         
cyborg4                                                                         
cyborg5                                                                         
cyborg6                                                                         
cyborg7                                                                         
cyborg8                                                                         
cyborg9                                                                         
cyborg10                                                                        
cyborg11                                                                        
cyborg12                                                                        
cyborg13                                                                        
cyborg14                                                                        
cyborg15                                                                        
Oracle1                                                                         
Oracle2                                                                         
Oracle3                                                                         
Oracle4                                                                         
Oracle5                                                                         
Oracle6                                                                         
Oracle7                                                                         
Oracle8                                                                         
Oracle9                                                                         
Oracle10                                                                        
Oracle11                                                                        
Oracle13                                                                        
Oracle14                                                                        
Oracle15                                                                        
Groot1                                                                          
Groot2                                                                          
Groot3                                                                          
Groot4                                                                          
Groot5                                                                          
Groot6                                                                          
Groot7                                                                          
Groot8                                                                          
Groot9                                                                          
Groot10                                                                         
Groot11                                                                         
Groot12                                                                         
Groot13                                                                         
Groot14                                                                         
Groot15                                                                         
Rondell, Aaron                                                                  
Rondinelli, Aaron                                                               
Rondo, Abbey                                                                    
Rondon, Abbie                                                                   
Rondy, Abby                                                                     
Rone, Abdul                                                                     
Roner, Abe                                                                      
Ronero, Abel                                                                    
Rones, Abigail                                                                  
Roney, Abraham                                                                  
Ronfeldt, Abram                                                                 
Rong, Ada                                                                       
Rongo, Adah                                                                     
Rongstad, Adalberto                                                             
Ronhaar, Adaline                                                                
Ronin, Adam                                                                     
Ronk, Adam                                                                      
Ronn, Adan                                                                      
Ronne, Addie                                                                    
Ronnfeldt, Adela                                                                
Ronnie, Adelaida                                                                
Ronning, Adelaide                                                               
Ronquillo, Adele                                                                
Rons, Adelia                                                                    
Ronsani, Adelina                                                                
Ronsini, Adeline                                                                
Ronson, Adell                                                                   
Ronzoni, Adella                                                                 
Rood, Adelle                                                                    
Roode, Adena                                                                    
Roof, Adina                                                                     
Roofe, Adolfo                                                                   
Roofner, Adolph                                                                 
Rook, Adria                                                                     
Rookard, Adrian                                                                 
Rooke, Adrian                                                                   
Rooker, Adriana                                                                 
Rooks, Adriane                                                                  
Rookstool, Adrianna                                                             
Rookwood, Adrianne                                                              
Room, Adrien                                                                    
Roome, Adriene                                                                  
Roon, Adrienne                                                                  
Rooney, Afton                                                                   
Roop, Agatha                                                                    
Roope, Agnes                                                                    
Roorda, Agnus                                                                   
Roos, Agripina                                                                  
Roosa, Agueda                                                                   
Roose, Agustin                                                                  
Roosevelt, Agustina                                                             
Root, Ahmad                                                                     
Rooth, Ahmed                                                                    
Roots, Ai                                                                       
Ropac, Aida                                                                     
Roper, Aide                                                                     
Ropers, Aiko                                                                    
Roperto, Aileen                                                                 
Ropes, Ailene                                                                   
Ropiski, Aimee                                                                  
Ropka, Aisha                                                                    
Ropp, Aja                                                                       
Roppolo, Akiko                                                                  
Roque, Akilah                                                                   
Roquemore, Al                                                                   
Roques, Alaina                                                                  
Rorabacher, Alaine                                                              
Rorabaugh, Alan                                                                 
Rorer, Alana                                                                    
Rorex, Alane                                                                    
Rorick, Alanna                                                                  
Rorie, Alayna                                                                   
Rork, Alba                                                                      
Rorrer, Albert                                                                  
Ros, Albert                                                                     
Rosa, Alberta                                                                   
Rosacker, Albertha                                                              
Rosada, Albertina                                                               
Rosado, Albertine                                                               
Rosal, Alberto                                                                  
Rosales, Albina                                                                 
Rosalez, Alda                                                                   
Rosamond, Alden                                                                 
Rosan, Aldo                                                                     
Rosander, Alease                                                                
Rosane, Alec                                                                    
Rosano, Alecia                                                                  
Rosario, Aleen                                                                  
Rosaro, Aleida                                                                  
Rosas, Aleisha                                                                  
Rosasco, Alejandra                                                              
Rosati, Alejandrina                                                             
Rosato, Alejandro                                                               
Rosavio, Alena                                                                  
Rosazza, Alene                                                                  
Rosberg, Alesha                                                                 
Rosboril, Aleshia                                                               
Rosborough, Alesia                                                              
Rosbough, Alessandra                                                            
Rosbozom, Aleta                                                                 
Rosca, Aletha                                                                   
Rosch, Alethea                                                                  
Roscigno, Alethia                                                               
Roscioli, Alex                                                                  
Roscoe, Alex                                                                    
Roscorla, Alexa                                                                 
Roscow, Alexander                                                               
Roscup, Alexander                                                               
Rose, Alexandra                                                                 
Rosebaugh, Alexandria                                                           
Roseberry, Alexia                                                               
Roseboom, Alexis                                                                
Roseboro, Alexis                                                                
Roseborough, Alfonso                                                            
Rosebrock, Alfonzo                                                              
Rosebrook, Alfred                                                               
Rosebrough, Alfreda                                                             
Rosebur, Alfredia                                                               
Rosebure, Alfredo                                                               
Rosebush, Ali                                                                   
Rosecrans, Ali                                                                  
Rosek, Alia                                                                     
Rosekrans, Alica                                                                
Rosel, Alice                                                                    
Roseland, Alicia                                                                
Roselius, Alida                                                                 
Rosell, Alina                                                                   
Rosella, Aline                                                                  
Roselle, Alisa                                                                  
Roselli, Alise                                                                  
Rosello, Alisha                                                                 
Roseman, Alishia                                                                
Rosemond, Alisia                                                                
Rosemore, Alison                                                                
Rosen, Alissa                                                                   
Rosenau, Alita                                                                  
Rosenbalm, Alix                                                                 
Rosenbarger, Aliza                                                              
Rosenbaum, Alla                                                                 
Rosenbeck, Allan                                                                
Rosenberg, Alleen                                                               
Rosenberger, Allegra                                                            
Rosenberry, Allen                                                               
Rosenblatt, Allen                                                               
Rosenbloom, Allena                                                              
Rosenblum, Allene                                                               
Rosenbluth, Allie                                                               
Rosenbrook, Alline                                                              
Rosenburg, Allison                                                              
Rosenbush, Allyn                                                                
Rosencrans, Allyson                                                             
Rosencrantz, Alma                                                               
Rosencranz, Almeda                                                              
Rosendahl, Almeta                                                               
Rosendale, Alona                                                                
Rosendo, Alonso                                                                 
Rosendorf, Alonzo                                                               
Rosene, Alpha                                                                   
Rosener, Alphonse                                                               
Rosenfeld, Alphonso                                                             
Rosenfeldt, Alta                                                                
Rosenfield, Altagracia                                                          
Rosengarten, Altha                                                              
Rosengren, Althea                                                               
Rosenhagen, Alton                                                               
Rosenheim, Alva                                                                 
Rosenholm, Alva                                                                 
Rosenkoetter, Alvaro                                                            
Rosenkrans, Alvera                                                              
Rosenkranz, Alverta                                                             
Rosenlof, Alvin                                                                 
Rosenow, Alvina                                                                 
Rosenquist, Alyce                                                               
Rosensteel, Alycia                                                              
Rosenstein, Alysa                                                               
Rosenstock, Alyse                                                               
Rosenthal, Alysha                                                               
Rosenthall, Alysia                                                              
Rosentrance, Alyson                                                             
Rosentrater, Alyssa                                                             
Rosenwald, Amada                                                                
Rosenwinkel, Amado                                                              
Rosenzweig, Amal                                                                
Roser, Amalia                                                                   
Rosero, Amanda                                                                  
Roses, Amber                                                                    
Rosete, Amberly                                                                 
Roseth, Ambrose                                                                 
Rosetta, Amee                                                                   
Rosette, Amelia                                                                 
Rosetti, America                                                                
Rosettie, Ami                                                                   
Roseum, Amie                                                                    
Rosewall, Amiee                                                                 
Rosewell, Amina                                                                 
Rosh, Amira                                                                     
Roshak, Ammie                                                                   
Roshannon, Amos                                                                 
Rosher, Amparo                                                                  
Roshia, Amy                                                                     
Rosi, An                                                                        
Rosiak, Ana                                                                     
Rosian, Anabel                                                                  
Rosica, Analisa                                                                 
Rosich, Anamaria                                                                
Rosie, Anastacia                                                                
Rosiek, Anastasia                                                               
Rosier, Andera                                                                  
Rosiles, Anderson                                                               
Rosillo, Andra                                                                  
Rosin, Andre                                                                    
Rosine, Andre                                                                   
Rosing, Andrea                                                                  
Rosinski, Andrea                                                                
Rositano, Andreas                                                               
Roskam, Andree                                                                  
Roske, Andres                                                                   
Roskelley, Andrew                                                               
Rosko, Andrew                                                                   
Roskop, Andria                                                                  
Roskopf, Andy                                                                   
Roskos, Anette                                                                  
Roskovensky, Angel                                                              
Roskowinski, Angel                                                              
Rosky, Angela                                                                   
Rosman, Angele                                                                  
Rosmarin, Angelena                                                              
Rosner, Angeles                                                                 
Roso, Angelia                                                                   
Rosoff, Angelic                                                                 
Rosol, Angelica                                                                 
Ross, Angelika                                                                  
Rossa, Angelina                                                                 
Rossano, Angeline                                                               
Rossbach, Angelique                                                             
Rosse, Angelita                                                                 
Rossean, Angella                                                                
Rosseau, Angelo                                                                 
Rosseel, Angelo                                                                 
Rossel, Angelyn                                                                 
Rossell, Angie                                                                  
Rosselle, Angila                                                                
Rosselli, Angla                                                                 
Rossen, Angle                                                                   
Rosser, Anglea                                                                  
Rosseter, Anh                                                                   
Rossetti, Anibal                                                                
Rossetto, Anika                                                                 
Rossey, Anisa                                                                   
Rossi, Anisha                                                                   
Rossie, Anissa                                                                  
Rossignol, Anita                                                                
Rossin, Anitra                                                                  
Rossing, Anja                                                                   
Rossingnol, Anjanette                                                           
Rossini, Anjelica                                                               
Rossiter, Ann                                                                   
Rossler, Anna                                                                   
Rossman, Annabel                                                                
Rossmann, Annabell                                                              
Rossmiller, Annabelle                                                           
Rossnagel, Annalee                                                              
Rosso, Annalisa                                                                 
Rosson, Annamae                                                                 
Rossotto, Annamaria                                                             
Rossow, Annamarie                                                               
Rossum, Anne                                                                    
Rost, Anneliese                                                                 
Rostad, Annelle                                                                 
Rostek, Annemarie                                                               
Rosten, Annett                                                                  
Roston, Annetta                                                                 
Rosu, Annette                                                                   
Rosul, Annice                                                                   
Roswell, Annie                                                                  
Roswick, Annika                                                                 
Roszales, Annis                                                                 
Roszel, Annita                                                                  
Roszell, Annmarie                                                               
Rota, Anthony                                                                   
Rotan, Anthony                                                                  
Rotando, Antione                                                                
Rotanelli, Antionette                                                           
Rotch, Antoine                                                                  
Rotchford, Antoinette                                                           
Rote, Anton                                                                     
Rotella, Antone                                                                 
Rotelli, Antonetta                                                              
Roten, Antonette                                                                
Rotenberg, Antonia                                                              
Rotenberry, Antonia                                                             
Rotering, Antonietta                                                            
Rotermund, Antonina                                                             
Rotert, Antonio                                                                 
Roth, Antonio                                                                   
Rothacher, Antony                                                               
Rothbart, Antwan                                                                
Rothbauer, Anya                                                                 
Rothberg, Apolonia                                                              
Rothchild, April                                                                
Rothe, Apryl                                                                    
Rothell, Ara                                                                    
Rothenbach, Araceli                                                             
Rothenberg, Aracelis                                                            
Rothenberger, Aracely                                                           
Rothenburger, Arcelia                                                           
Rother, Archie                                                                  
Rotherham, Ardath                                                               
Rothermel, Ardelia                                                              
Rothermich, Ardell                                                              
Rothery, Ardella                                                                
Rothfeld, Ardelle                                                               
Rothfus, Arden                                                                  
Rothfuss, Ardis                                                                 
Rothgaber, Ardith                                                               
Rothgeb, Aretha                                                                 
Rothgery, Argelia                                                               
Rothhaupt, Argentina                                                            
Rothlisberger, Ariana                                                           
Rothman, Ariane                                                                 
Rothmann, Arianna                                                               
Rothmiller, Arianne                                                             
Rothove, Arica                                                                  
Rothrock, Arie                                                                  
Rothschild, Ariel                                                               
Rothstein, Ariel                                                                
Rothweiler, Arielle                                                             
Rothwell, Arla                                                                  
Rotkovecz, Arlean                                                               
Rotkowski, Arleen                                                               
Rotman, Arlen                                                                   
Rotner, Arlena                                                                  
Rotolo, Arlene                                                                  
Roton, Arletha                                                                  
Rotondi, Arletta                                                                
Rotondo, Arlette                                                                
Rotramel, Arlie                                                                 
Rotruck, Arlinda                                                                
Rotstein, Arline                                                                
Rott, Arlyne                                                                    
Rottenberg, Armand                                                              
Rotter, Armanda                                                                 
Rottier, Armandina                                                              
Rottinghaus, Armando                                                            
Rottinghous, Armida                                                             
Rottman, Arminda                                                                
Rottner, Arnetta                                                                
Rotton, Arnette                                                                 
Rotty, Arnita                                                                   
Rotunda, Arnold                                                                 
Rotundo, Arnoldo                                                                
Rotunno, Arnulfo                                                                
Rotz, Aron                                                                      
Roubekas, Arron                                                                 
Rouch, Art                                                                      
Roucoulet, Arthur                                                               
Roudabush, Arthur                                                               
Roudebush, Artie                                                                
Roudybush, Arturo                                                               
Rouff, Arvilla                                                                  
Roufs, Asa                                                                      
Rouge, Asha                                                                     
Rougeau, Ashanti                                                                
Rougeaux, Ashely                                                                
Rougeot, Ashlea                                                                 
Rough, Ashlee                                                                   
Roughen, Ashleigh                                                               
Rought, Ashley                                                                  
Roughton, Ashley                                                                
Rougier, Ashli                                                                  
Rouhoff, Ashlie                                                                 
Rouillard, Ashly                                                                
Rouillier, Ashlyn                                                               
Rouisse, Ashton                                                                 
Roule, Asia                                                                     
Rouleau, Asley                                                                  
Roulette, Assunta                                                               
Roulhac, Astrid                                                                 
Roulston, Asuncion                                                              
Rouly, Athena                                                                   
Roumeliotis, Aubrey                                                             
Round, Aubrey                                                                   
Roundabush, Audie                                                               
Rounds, Audra                                                                   
Roundtree, Audrea                                                               
Roundy, Audrey                                                                  
Rounkles, Audria                                                                
Rounsaville, Audrie                                                             
Rounsville, Audry                                                               
Rountree, August                                                                
Roup, Augusta                                                                   
Roupe, Augustina                                                                
Roura, Augustine                                                                
Rourk, Augustine                                                                
Rourke, Augustus                                                                
Rous, Aundrea                                                                   
Rousch, Aura                                                                    
Rouse, Aurea                                                                    
Rousell, Aurelia                                                                
Rouselle, Aurelio                                                               
Rouser, Aurora                                                                  
Rousey, Aurore                                                                  
Roush, Austin                                                                   
Rousse, Austin                                                                  
Rousseau, Autumn                                                                
Roussel, Ava                                                                    
Roussell, Avelina                                                               
Rousselle, Avery                                                                
Roussin, Avery                                                                  
Rousso, Avis                                                                    
Roussos, Avril                                                                  
Rousu, Awilda                                                                   
Rout, Ayako                                                                     
Route, Ayana                                                                    
Routh, Ayanna                                                                   
Routhier, Ayesha                                                                
Routledge, Azalee                                                               
Routon, Azucena                                                                 
Routson, Azzie                                                                  
Routt, Babara                                                                   
Routte, Babette                                                                 
Routzahn, Bailey                                                                
Routzen, Bambi                                                                  
Rouw, Bao                                                                       
Roux, Barabara                                                                  
Rouzer, Barb                                                                    
Rouzzo, Barbar                                                                  
Rovack, Barbara                                                                 
Rovell, Barbera                                                                 
Rovella, Barbie                                                                 
Rovelto, Barbra                                                                 
Rover, Bari                                                                     
Rovere, Barney                                                                  
Rovero, Barrett                                                                 
Rovinsky, Barrie                                                                
Rovira, Barry                                                                   
Rovner, Bart                                                                    
Row, Barton                                                                     
Rowald, Basil                                                                   
Rowan, Basilia                                                                  
Rowand, Bea                                                                     
Rowback, Beata                                                                  
Rowbotham, Beatrice                                                             
Rowbottom, Beatris                                                              
Rowcliffe, Beatriz                                                              
Rowden, Beau                                                                    
Rowe, Beaulah                                                                   
Rowell, Bebe                                                                    
Rowels, Becki                                                                   
Rowen, Beckie                                                                   
Rower, Becky                                                                    
Rowett, Bee                                                                     
Rowey, Belen                                                                    
Rowland, Belia                                                                  
Rowlands, Belinda                                                               
Rowlee, Belkis                                                                  
Rowles, Bell                                                                    
Rowlett, Bella                                                                  
Rowlette, Belle                                                                 
Rowley, Belva                                                                   
Rowling, Ben                                                                    
Rowlins, Benedict                                                               
Rowlison, Benita                                                                
Rowls, Benito                                                                   
Rowman, Benjamin                                                                
Rownd, Bennett                                                                  
Rowntree, Bennie                                                                
Rowold, Bennie                                                                  
Rowray, Benny                                                                   
Rowse, Benton                                                                   
Rowsell, Berenice                                                               
Rowser, Berna                                                                   
Rowsey, Bernadette                                                              
Rowson, Bernadine                                                               
Rowton, Bernard                                                                 
Rowzee, Bernarda                                                                
Rox, Bernardina                                                                 
Roxas, Bernardine                                                               
Roxberry, Bernardo                                                              
Roxburgh, Berneice                                                              
Roxbury, Bernetta                                                               
Roy, Bernice                                                                    
Roya, Bernie                                                                    
Royal, Bernie                                                                   
Royall, Berniece                                                                
Royals, Bernita                                                                 
Royalty, Berry                                                                  
Roybal, Berry                                                                   
Royce, Bert                                                                     
Roye, Berta                                                                     
Royea, Bertha                                                                   
Royer, Bertie                                                                   
Roylance, Bertram                                                               
Royle, Beryl                                                                    
Roys, Bess                                                                      
Roysden, Bessie                                                                 
Royse, Beth                                                                     
Royster, Bethanie                                                               
Royston, Bethann                                                                
Serino, Marylou                                                                 
Serio, Marylouise                                                               
Serisky, Marylyn                                                                
Serl, Marylynn                                                                  
Serles, Maryrose                                                                
Sermania, Masako                                                                
Sermeno, Mason                                                                  
Sermersheim, Matha                                                              
Sermon, Mathew                                                                  
Sermons, Mathilda                                                               
Serna, Mathilde                                                                 
Sernas, Matilda                                                                 
Sero, Matilde                                                                   
Seroka, Matt                                                                    
Serpa, Matthew                                                                  
Serpas, Matthew                                                                 
Serpe, Mattie                                                                   
Serpico, Maud                                                                   
Serr, Maude                                                                     
Serra, Maudie                                                                   
Serramo, Maura                                                                  
Serrand, Maureen                                                                
Serrano, Maurice                                                                
Serrant, Maurice                                                                
Serrao, Mauricio                                                                
Serrata, Maurine                                                                
Serrato, Maurita                                                                
Serratore, Mauro                                                                
Serratos, Mavis                                                                 
Serravalli, Max                                                                 
Serre, Maxie                                                                    
Serrell, Maxima                                                                 
Serres, Maximina                                                                
Serret, Maximo                                                                  
Serrett, Maxine                                                                 
Serrin, Maxwell                                                                 
Serro, May                                                                      
Sers, Maya                                                                      
Sersen, Maybell                                                                 
Sert, Maybelle                                                                  
Sertuche, Maye                                                                  
Serum, Mayme                                                                    
Serva, Maynard                                                                  
Servais, Mayola                                                                 
Servan, Mayra                                                                   
Servano, Mazie                                                                  
Servant, Mckenzie                                                               
Servantes, Mckinley                                                             
Servantez, Meagan                                                               
Servatius, Meaghan                                                              
Serve, Mechelle                                                                 
Servedio, Meda                                                                  
Servello, Mee                                                                   
Serven, Meg                                                                     
Server, Megan                                                                   
Servey, Meggan                                                                  
Servi, Meghan                                                                   
Service, Meghann                                                                
Servidio, Mei                                                                   
Serville, Mel                                                                   
Servin, Melaine                                                                 
Servino, Melani                                                                 
Servis, Melania                                                                 
Serviss, Melanie                                                                
Servoss, Melany                                                                 
Seryak, Melba                                                                   
Sesareo, Melda                                                                  
Sesay, Melia                                                                    
Sesco, Melida                                                                   
Sesko, Melina                                                                   
Sesler, Melinda                                                                 
Sesley, Melisa                                                                  
Sesma, Melissa                                                                  
Sespinosa, Melissia                                                             
Sessa, Melita                                                                   
Sesser, Mellie                                                                  
Sessin, Mellisa                                                                 
Session, Mellissa                                                               
Sessions, Melodee                                                               
Sessler, Melodi                                                                 
Sesso, Melodie                                                                  
Sessom, Melody                                                                  
Sessoms, Melonie                                                                
Sessum, Melony                                                                  
Sessums, Melva                                                                  
Sester, Melvin                                                                  
Sestoso, Melvin                                                                 
Seta, Melvina                                                                   
Setaro, Melynda                                                                 
Setchell, Mendy                                                                 
Setera, Mercedes                                                                
Seth, Mercedez                                                                  
Sether, Mercy                                                                   
Sethi, Meredith                                                                 
Seti, Meri                                                                      
Setias, Merideth                                                                
Setlak, Meridith                                                                
Setler, Merilyn                                                                 
Setliff, Merissa                                                                
Setlock, Merle                                                                  
Seto, Merle                                                                     
Seton, Merlene                                                                  
Setser, Merlin                                                                  
Sette, Merlyn                                                                   
Settecase, Merna                                                                
Setter, Merri                                                                   
Setterberg, Merrie                                                              
Setterland, Merrilee                                                            
Setters, Merrill                                                                
Settimo, Merrill                                                                
Setting, Merry                                                                  
Settino, Mertie                                                                 
Settle, Mervin                                                                  
Settlemire, Meryl                                                               
Settlemires, Meta                                                               
Settlemyre, Mi                                                                  
Settler, Mia                                                                    
Settles, Mica                                                                   
Setton, Micaela                                                                 
Setty, Micah                                                                    
Setzer, Micah                                                                   
Setzler, Micha                                                                  
Seu, Michael                                                                    
Seubert, Michael                                                                
Seuell, Michaela                                                                
Seufer, Michaele                                                                
Seufert, Michal                                                                 
Seumanu, Michal                                                                 
Seung, Michale                                                                  
Seurer, Micheal                                                                 
Seuss, Micheal                                                                  
Seutter, Michel                                                                 
Sevaaetasi, Michel                                                              
Sevadjian, Michele                                                              
Sevcik, Michelina                                                               
Sevedge, Micheline                                                              
Sevenbergen, Michell                                                            
Seveney, Michelle                                                               
Sever, Michiko                                                                  
Severa, Mickey                                                                  
Severance, Mickey                                                               
Severe, Micki                                                                   
Severi, Mickie                                                                  
Severin, Miesha                                                                 
Severino, Migdalia                                                              
Severn, Mignon                                                                  
Severns, Miguel                                                                 
Severo, Miguelina                                                               
Severs, Mika                                                                    
Severson, Mikaela                                                               
Severt, Mike                                                                    
Severtson, Mike                                                                 
Severy, Mikel                                                                   
Severyn, Miki                                                                   
Sevey, Mikki                                                                    
Sevick, Mila                                                                    
Sevier, Milagro                                                                 
Sevigny, Milagros                                                               
Sevilla, Milan                                                                  
Sevillano, Milda                                                                
Seville, Mildred                                                                
Sevin, Miles                                                                    
Sevy, Milford                                                                   
Sewade, Milissa                                                                 
Sewald, Millard                                                                 
Sewall, Millicent                                                               
Seward, Millie                                                                  
Seweall, Milly                                                                  
Sewell, Milo                                                                    
Sewer, Milton                                                                   
Sewester, Mimi                                                                  
Sewyerd, Min                                                                    
Sexauer, Mina                                                                   
Sexson, Minda                                                                   
Sexton, Mindi                                                                   
Sey, Mindy                                                                      
Seyal, Minerva                                                                  
Seyb, Ming                                                                      
Seybert, Minh                                                                   
Seybold, Minh                                                                   
Seydel, Minna                                                                   
Seyer, Minnie                                                                   
Seyfarth, Minta                                                                 
Seyfert, Miquel                                                                 
Seyfried, Mira                                                                  
Seykora, Miranda                                                                
Seykoski, Mireille                                                              
Seyler, Mirella                                                                 
Seyller, Mireya                                                                 
Seymer, Miriam                                                                  
Seymor, Mirian                                                                  
Seymore, Mirna                                                                  
Seymour, Mirta                                                                  
Seymoure, Mirtha                                                                
Seys, Misha                                                                     
Sfatcu, Miss                                                                    
Sfera, Missy                                                                    
Sferra, Misti                                                                   
Sferrazza, Mistie                                                               
Sforza, Misty                                                                   
Sgambati, Mitch                                                                 
Sgammato, Mitchel                                                               
Sgrignoli, Mitchell                                                             
Sgro, Mitchell                                                                  
Sgroi, Mitsue                                                                   
Sgueglia, Mitsuko                                                               
Sha, Mittie                                                                     
Shaak, Mitzi                                                                    
Shabala, Mitzie                                                                 
Shaban, Miyoko                                                                  
Shabazz, Modesta                                                                
Shabel, Modesto                                                                 
Shaben, Mohamed                                                                 
Shabot, Mohammad                                                                
Shack, Mohammed                                                                 
Shackelford, Moira                                                              
Shackelton, Moises                                                              
Shackett, Mollie                                                                
Shackford, Molly                                                                
Shackle, Mona                                                                   
Shackleford, Monet                                                              
Shackleton, Monica                                                              
Shacklett, Monika                                                               
Shackley, Monique                                                               
Shad, Monnie                                                                    
Shadazz, Monroe                                                                 
Shadburn, Monserrate                                                            
Shadd, Monte                                                                    
Shadden, Monty                                                                  
Shadding, Moon                                                                  
Shaddix, Mora                                                                   
Shaddock, Morgan                                                                
Shaddox, Morgan                                                                 
Shadduck, Moriah                                                                
Shade, Morris                                                                   
Shader, Morton                                                                  
Shadfar, Mose                                                                   
Shadiack, Moses                                                                 
Shadid, Moshe                                                                   
Shadix, Mozell                                                                  
Shadle, Mozella                                                                 
Shadler, Mozelle                                                                
Shadley, Mui                                                                    
Shadoan, Muoi                                                                   
Shadow, Muriel                                                                  
Shadowens, Murray                                                               
Shadrick, My                                                                    
Shadwell, Myesha                                                                
Shadwick, Myles                                                                 
Shady, Myong                                                                    
Shae, Myra                                                                      
Shaefer, Myriam                                                                 
Shaeffer, Myrl                                                                  
Shaer, Myrle                                                                    
Shafe, Myrna                                                                    
Shafer, Myron                                                                   
Shaff, Myrta                                                                    
Shaffen, Myrtice                                                                
Shaffer, Myrtie                                                                 
Shaffner, Myrtis                                                                
Shaffren, Myrtle                                                                
Shaffstall, Myung                                                               
Shafi, Na                                                                       
Shafran, Nada                                                                   
Shaftic, Nadene                                                                 
Shafto, Nadia                                                                   
Shaggy, Nadine                                                                  
Shaginaw, Naida                                                                 
Shah, Nakesha                                                                   
Shahan, Nakia                                                                   
Shahbaz, Nakisha                                                                
Shaheed, Nakita                                                                 
Shaheen, Nam                                                                    
Shahid, Nan                                                                     
Shahim, Nana                                                                    
Shahin, Nancee                                                                  
Shahinfar, Nancey                                                               
Shahinian, Nanci                                                                
Shaikh, Nancie                                                                  
Shain, Nancy                                                                    
Shake, Nanette                                                                  
Shaker, Nannette                                                                
Shakespear, Nannie                                                              
Shakespeare, Naoma                                                              
Shakin, Naomi                                                                   
Shakir, Napoleon                                                                
Shaklee, Narcisa                                                                
Shakoor, Natacha                                                                
Shala, Natalia                                                                  
Shalam, Natalie                                                                 
Shalash, Natalya                                                                
Shalhoub, Natasha                                                               
Shalhoup, Natashia                                                              
Shaline, Nathalie                                                               
Shall, Nathan                                                                   
Shalla, Nathanael                                                               
Shallcross, Nathanial                                                           
Shallenberger, Nathani...                                                       
Shallow, Natisha                                                                
Shalwani, Natividad                                                             
Sham, Natosha                                                                   
Shamapande, Neal                                                                
Shamas, Necole                                                                  
Shambaugh, Ned                                                                  
Shambley, Neda                                                                  
Shamblin, Nedra                                                                 
Shambo, Neely                                                                   
Shambrook, Neida                                                                
Shamburg, Neil                                                                  
Shamburger, Nelda                                                               
Shamel, Nelia                                                                   
Shames, Nelida                                                                  
Shami, Nell                                                                     
Shamily, Nella                                                                  
Shamir, Nelle                                                                   
Shamlin, Nellie                                                                 
Shammaa, Nelly                                                                  
Shammah, Nelson                                                                 
Shammo, Nena                                                                    
Shamonsky, Nenita                                                               
Shamp, Neoma                                                                    
Shampine, Neomi                                                                 
Shams, Nereida                                                                  
Shamsi, Nerissa                                                                 
Shamsiddeen, Nery                                                               
Shan, Nestor                                                                    
Shanaa, Neta                                                                    
Shanafelt, Nettie                                                               
Shanahan, Neva                                                                  
Shanberg, Nevada                                                                
Shand, Neville                                                                  
Shandley, Newton                                                                
Shandro, Nga                                                                    
Shands, Ngan                                                                    
Shandy, Ngoc                                                                    
Shane, Nguyet                                                                   
Shaner, Nia                                                                     
Shaneyfelt, Nichelle                                                            
Shangraw, Nichol                                                                
Shanholtz, Nicholas                                                             
Shanholtzer, Nichole                                                            
Shani, Nicholle                                                                 
Shank, Nick                                                                     
Shanker, Nicki                                                                  
Shankin, Nickie                                                                 
Shankland, Nickolas                                                             
Shankle, Nickole                                                                
Shankles, Nicky                                                                 
Gapinski, Nicky                                                                 
Gapp, Nicol                                                                     
Gappa, Nicola                                                                   
Gara, Nicolas                                                                   
Garabedian, Nicolasa                                                            
Garacci, Nicole                                                                 
Garacia, Nicolette                                                              
Garafalo, Nicolle                                                               
Garafano, Nida                                                                  
Garafola, Nidia                                                                 
Garahan, Niesha                                                                 
Garala, Nieves                                                                  
Garan, Nigel                                                                    
Garand, Niki                                                                    
Garant, Nikia                                                                   
Garasha, Nikita                                                                 
Garate, Nikki                                                                   
Garavaglia, Nikole                                                              
Garavelli, Nila                                                                 
Garaventa, Nilda                                                                
Garay, Nilsa                                                                    
Garb, Nina                                                                      
Garbacz, Ninfa                                                                  
Garbarini, Nisha                                                                
Garbarino, Nita                                                                 
Garbe, Noah                                                                     
Garber, Noble                                                                   
Garbett, Nobuko                                                                 
Garbin, Noe                                                                     
Garbo, Noel                                                                     
Garbutt, Noel                                                                   
Garcea, Noelia                                                                  
Garceau, Noella                                                                 
Garced, Noelle                                                                  
Garcelon, Noemi                                                                 
Garces, Nohemi                                                                  
Garcia, Nola                                                                    
Garcias, Nolan                                                                  
Garcilazo, Noma                                                                 
Garcon, Nona                                                                    
Garcy, Nora                                                                     
Garczynski, Norah                                                               
Gard, Norbert                                                                   
Garde, Norberto                                                                 
Gardea, Noreen                                                                  
Gardecki, Norene                                                                
Gardella, Noriko                                                                
Gardemal, Norine                                                                
Garden, Norma                                                                   
Gardenas, Norman                                                                
Gardener, Norman                                                                
Gardenhire, Normand                                                             
Garder, Norris                                                                  
Gardin, Nova                                                                    
Gardiner, Novella                                                               
Garding, Nu                                                                     
Gardinier, Nubia                                                                
Gardino, Numbers                                                                
Gardley, Numbers                                                                
Gardner, Nydia                                                                  
Gardocki, Nyla                                                                  
Gardon, Obdulia                                                                 
Gardunio, Ocie                                                                  
Garduno, Octavia                                                                
Gardy, Octavio                                                                  
Gareau, Oda                                                                     
Garelick, Odelia                                                                
Garelik, Odell                                                                  
Garen, Odell                                                                    
Gares, Odessa                                                                   
Garetson, Odette                                                                
Garett, Odilia                                                                  
Garey, Odis                                                                     
Garf, Ofelia                                                                    
Garff, Ok                                                                       
Garfias, Ola                                                                    
Garfield, Olen                                                                  
Garfinkel, Olene                                                                
Garfinkle, Oleta                                                                
Garfunkel, Olevia                                                               
Garg, Olga                                                                      
Gargan, Olimpia                                                                 
Gargani, Olin                                                                   
Gargano, Olinda                                                                 
Gargis, Oliva                                                                   
Gargiulo, Olive                                                                 
Garguilo, Oliver                                                                
Gargus, Olivia                                                                  
Garhart, Ollie                                                                  
Gari, Ollie                                                                     
Garia, Olympia                                                                  
Garib, Oma                                                                      
Garibai, Omar                                                                   
Garibaldi, Omega                                                                
Garibaldo, Omer                                                                 
Garibay, Ona                                                                    
Garica, Oneida                                                                  
Garich, Onie                                                                    
Garick, Onita                                                                   
Gariepy, Opal                                                                   
Gariety, Ophelia                                                                
Garigen, Ora                                                                    
Garigliano, Oralee                                                              
Garin, Oralia                                                                   
Garing, Oren                                                                    
Garinger, Oretha                                                                
Garis, Orlando                                                                  
Gariti, Orpha                                                                   
Garito, Orval                                                                   
Garitty, Orville                                                                
Garity, Oscar                                                                   
Garivay, Oscar                                                                  
Garkow, Ossie                                                                   
Garland, Osvaldo                                                                
Garlett, Oswaldo                                                                
Garley, Otelia                                                                  
Garlick, Otha                                                                   
Garling, Otha                                                                   
Garlinger, Otilia                                                               
Garlington, Otis                                                                
Garlits, Otto                                                                   
Garlitz, Ouida                                                                  
Garlock, Owen                                                                   
Garlovsky, Ozell                                                                
Garlow, Ozella                                                                  
Garman, Ozie                                                                    
Garmany, Pa                                                                     
Garmen, Pablo                                                                   
Garmire, Page                                                                   
Garmoe, Paige                                                                   
Garmon, Palma                                                                   
Garms, Palmer                                                                   
Garn, Palmira                                                                   
Garnache, Pam                                                                   
Garnand, Pamala                                                                 
Garnder, Pamela                                                                 
Garneau, Pamelia                                                                
Garner, Pamella                                                                 
Garnes, Pamila                                                                  
Garness, Pamula                                                                 
Garnet, Pandora                                                                 
Garnett, Pansy                                                                  
Garnette, Paola                                                                 
Garney, Paris                                                                   
Garnham, Paris                                                                  
Garnica, Parker                                                                 
Garnick, Parthenia                                                              
Garnier, Particia                                                               
Garno, Pasquale                                                                 
Groot                                                                           
Airwolf                                                                         
Rogers, Chris                                                                   
Prindel                   a...                                                  
scripty                                                                         
Oracle12                                                                                                                        
```
We check again to see if it is an encoded Powershell command and to make sure that this Prindel person has only their last name listed here. And the output tracks! (I skipped the unnecessary output)
```powershell
PS C:\users\trebek13\desktop> Get-ADUser -Properties City -Filter *
City              : agBvAGkAbgBfAHQAaABlAF8AcgBlAGIAZQBsAHMA                    
DistinguishedName : CN=Prindel,OU=T-65,OU=X-Wing,DC=underthewire,DC=tech        
Enabled           : False                                                       
GivenName         : Prindel                                                     
Name              : Prindel                                                     
ObjectClass       : user                                                        
ObjectGUID        : 8edb88c2-c69b-4d78-957e-6c1d1b08f2a5                        
SamAccountName    : Prindel                                                     
SID               : S-1-5-21-758131494-606461608-3556270690-2178                
Surname           : Prindel                                                     
UserPrincipalName : Prindel
```
<strong>Password:</strong> <code>prindel3003</code>
