# Roland Garros

1. Entradas precisam ser valores na base 2 por que precisamos garantir que o valor seja sempre par;
2. O número total de partidas é o número total de participantes - 1, por ser mata-mata, todos perdem pelo menos uma vez, menos o vencedor;
3. O número de rodadas é o expoente - 1 na base 2, considerando que k =  expoente - 1, portanto log de n na base 2. 

# Cavalo

![[Pasted image 20250901183010.png]]

1. Definir estruturas auxiliares:
	1. Molde contendo os movimentos legais do cavalo;
	2. Construção do tabuleiro com uma matriz na qual 0 são as casas não acessadas, 1 as acessadas e -1 as casas ilegais;
	3. classe Nó, contendo linha e coluna que o nó esta posicionado;
	4. classe Resultado, contendo a distância percorrida e o caminho reconstruído.
2. Inicializar o tabuleiro colocando o ponto de partida com distância 0;
3. Enfileira 