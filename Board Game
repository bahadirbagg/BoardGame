#include <string.h>
#include <stdlib.h>
#include <stdbool.h>
#include <time.h>
#define MAX_LIMIT 20
int totalmoveX(char board[7][7]);
int totalmoveO(char board[7][7]);
void getBoard(int pieces, char board[7][7]);
void printBoard(char board[7][7]);
void move(char board[7][7], int playerNum, int turn);		
int aiO(char board[7][7], int player, int numPieces, int max,int cond);
int aiX(char board[7][7], int player, int numPieces, int max,int cond);

int main(){
	char board[7][7];
	int turn,pieces,player,max,user,start,i,j;
	int cond=0;
	printf("Enter the turn: ");
	scanf("%d", &turn);
	printf("Enter the piece number: ");
	scanf("%d", &pieces);
	printf("Enter 1 to play as X     2 to play as O: ");
	scanf("%d", &player);
	printf("Enter 1 to start first     2 to start second: ");
	scanf("%d", &start);
	
	if(player==1){
		user=1;
		printf("\n *******YOUR PIECE IS X*********\n");
	}
    else if(player==2){
		user=2;
		printf("\n *******YOUR PIECE IS O*********\n");
	}
	else{
		printf("\n Wrong Number\n");
		return -1;
	}
	getBoard(pieces, board);
	printBoard(board);
	int movex=totalmoveX(board);							//total moves for x
	printf("TOTAL MOVES OF X %d\n",movex);
	int moveo=totalmoveO(board);							//total moves for o
	printf("TOTAL MOVES OF O %d\n",moveo);
	
	if(start==1){
		if(user==1){
			int aimove;
			while(turn > 0){
				move(board, player, turn);                                //user move
				printBoard(board);
				movex=totalmoveX(board);							//total moves for x
				printf("TOTAL MOVES OF X %d\n",movex);
				moveo=totalmoveO(board);							//total moves for o
				printf("TOTAL MOVES OF O %d\n",moveo);
				aimove = aiO(board, player, pieces, max, cond);	  //ai move
				printBoard(board);
				turn--;
				movex=totalmoveX(board);							//total moves for x
				printf("TOTAL MOVES OF X %d\n",movex);
				moveo=totalmoveO(board);							//total moves for o
				printf("TOTAL MOVES OF O %d\n",moveo);
				if(turn==0){											    //cheks for turn and win condition
					if(movex>moveo){
						printf("\n X WIN \n");
					}
					else if(moveo>movex){
						printf("\n O WIN \n");
					}
					else if(moveo==movex){
						printf("\n DRAW \n");
					}
					return 0;
				}
					printf("\n*****%d turn left*****\n",turn);				//turn calculator
			}
		}
		if(user==2){
			int aimove;
			while(turn > 0){
				move(board, player, turn);                                //user move
				printBoard(board);
				movex=totalmoveX(board);							//total moves for x
				printf("TOTAL MOVES OF X %d\n",movex);
				moveo=totalmoveO(board);							//total moves for o
				printf("TOTAL MOVES OF O %d\n",moveo);
				aimove = aiX(board, player, pieces, max, cond);	  //ai move
				printBoard(board);
				turn--;
				int movex=totalmoveX(board);							//total moves for x
				printf("TOTAL MOVES OF X %d\n",movex);
				int moveo=totalmoveO(board);							//total moves for o
				printf("TOTAL MOVES OF O %d\n",moveo);
				if(turn==0){											    //cheks for turn and win condition
					if(movex>moveo){
						printf("\n X WIN \n");
					}
					else if(moveo>movex){
						printf("\n O WIN \n");
					}
					else if(moveo==movex){
						printf("\n DRAW \n");
					}
					return 0;
				}
					printf("\n*****%d turn left*****\n",turn);				//turn calculator
			}
		}
	}
	else if(start==2){
		if(user==1){
			int aimove;
			while(turn > 0){
				aimove = aiO(board, player, pieces, max,cond);		//ai move
				printBoard(board);
				movex=totalmoveX(board);							//total moves for x
				printf("TOTAL MOVES OF X %d\n",movex);
				moveo=totalmoveO(board);							//total moves for o
				printf("TOTAL MOVES OF 0 %d\n",moveo);
				move(board, player, turn);								 //user move
				printBoard(board);
				turn--;
				movex=totalmoveX(board);
				printf("TOTAL MOVES OF X %d\n",movex);
				moveo=totalmoveO(board);
				printf("TOTAL MOVES OF 0 %d\n",moveo);
				if(turn==0){                                                 //cheks for turn and win condition
					if(movex>moveo){
						printf("\n X WIN \n");
					}
					else if(moveo>movex){
						printf("\n o WIN \n");
					}
					else if(moveo==movex){
						printf("\n DRAW \n");
					}
					return 0;
				}
				printf("\n*****%d turn left*****\n",turn);					//turn calculator
			}
		}
		if(user==2){
			int aimove;
			while(turn > 0){
				aimove = aiX(board, player, pieces, max,cond);		//ai move
				printBoard(board);
				movex=totalmoveX(board);							//total moves for x
				printf("TOTAL MOVES OF X %d\n",movex);
				moveo=totalmoveO(board);							//total moves for o
				printf("TOTAL MOVES OF O %d\n",moveo);
				move(board, player, turn);								 //user move
				printBoard(board);
				turn--;
				movex=totalmoveX(board);
				printf("TOTAL MOVES OF X %d\n",movex);
				moveo=totalmoveO(board);
				printf("TOTAL MOVES OF O %d\n",moveo);
				if(turn==0){                                                 //cheks for turn and win condition
					if(movex>moveo){
						printf("\n X WIN \n");
					}
					else if(moveo>movex){
						printf("\n O WIN \n");
					}
					else if(moveo==movex){
						printf("\n DRAW \n");
					}
					return 0;
				}
				printf("\n*****%d turn left*****\n",turn);					//turn calculator
			}
		}
	}
	return 0;
}
int aiO(char board[7][7], int player, int pieces, int max,int cond){
	int bestmax,moves,i,j;
	int firstO=0;
	int d=1;
	int a[4];
	int numpiececheck=0;
	char tmpBoard[7][7],tmpBoard1[7][7],tmpBoard2[7][7],tmpBoard3[7][7];
	
	if(player == 1){
		for(i=0;i<7;i++){
			for(j=0;j<7;j++){
				if(board[i][j] == 'O'){													//checks for O pieces in board
					int moves1=0,moves2=0,moves3=0,moves4=0;
					pieces--;
					firstO++;
					if(j != 0 && board[i][j-1] == '-'){									//checks left side of O token
						memcpy(tmpBoard, board, 7*7*sizeof(char));
						tmpBoard[i][j-1] = 'O';
						tmpBoard[i][j] = '-';
						moves1=totalmoveO(tmpBoard);
					
							    									
					}
					if(i != 6 && board[i+1][j] == '-'){										//checks down side of O token
						memcpy(tmpBoard1, board, 7*7*sizeof(char));
						tmpBoard1[i+1][j] = 'O';
						tmpBoard1[i][j] = '-';
						moves2=totalmoveO(tmpBoard1);
				
							
					}
					if(j != 6 && board[i][j+1] == '-'){											//checks right side of O token
						memcpy(tmpBoard2, board, 7*7*sizeof(char));
						tmpBoard2[i][j+1] = 'O';
						tmpBoard2[i][j] = '-';
						moves3=totalmoveO(tmpBoard2);
					
								
					}
					if(i != 0 && board[i-1][j] == '-'){											//checks upper side of O token
						memcpy(tmpBoard3, board, 7*7*sizeof(char));
						tmpBoard3[i-1][j] = 'O';
						tmpBoard3[i][j] = '-';
						moves4=totalmoveO(tmpBoard3);
				
					
						}
						a[0]=moves1;
						a[1]=moves2;
						a[2]=moves3;
						a[3]=moves4;
						
						for(int n=0;n<4;n++)
						{
							if((max)>(a[n]))
							{ 
								
							}
							else
							{
								max = (a[n]); 
							
							}	
						}
					
						if(firstO==d && cond==0){                                      //gets upmost O tokens max move value
							d++;
							bestmax=max;
						
							max=bestmax;              								//getting for the best move for all 0 tokens
						}	
						bestmax=max;												
						if(cond==1){    
				                               							 
							if(bestmax==a[0]){
								memcpy(board, tmpBoard, 7*7*sizeof(char));
								printf("\n***** AI moved %dth O piece to left*****\n",firstO);
							
								cond++;
								break;
							}
							else if(bestmax==a[1]){
								memcpy(board, tmpBoard1, 7*7*sizeof(char));
								printf("\n***** AI moved %dth O piece to down*****\n",firstO);
							
								cond++;
								break;
							}
							else if(bestmax==a[2]){
								memcpy(board, tmpBoard2, 7*7*sizeof(char));
								printf("\n***** AI moved %dth O piece to right*****\n",firstO);
						
								cond++;
								break;
							}
							else if(bestmax==a[3]){
								memcpy(board, tmpBoard3, 7*7*sizeof(char));
								printf("\n***** AI moved %dth O piece to up*****\n",firstO);
							
								cond++;
								break;
							}
							
						}	
					}
				}
			}
		
			if(max==a[0] && cond==0){
				memcpy(board, tmpBoard, 7*7*sizeof(char));
				printf("\n***** AI moved %dth O piece to left*****\n",firstO);
			
				numpiececheck=1;
			}
			else if(max==a[1] && cond==0){
				memcpy(board, tmpBoard1, 7*7*sizeof(char));
				printf("\n***** AI moved %dth O piece to down*****\n",firstO);
			
				numpiececheck=1;
			}
			else if(max==a[2] && cond==0){
				memcpy(board, tmpBoard2, 7*7*sizeof(char));
				printf("\n***** AI moved %dth O piece to right*****\n",firstO);
		
				numpiececheck=1;
			}
			else if(max==a[3] && cond==0){
				memcpy(board, tmpBoard3, 7*7*sizeof(char));
				printf("\n***** AI moved %dth O piece to up*****\n",firstO);
			
				numpiececheck=1;
			}
			else if(pieces==0 && numpiececheck==0){
			
				int r=aiO(board, 1, pieces, max,cond+1);                //++condt
				return r;
			}	
			
		}
	}
int aiX(char board[7][7], int player, int pieces, int max,int cond){	
	int bestmax,moves,i,j;
	int firstO=0;
	int d=1;
	int a[4];
	int numpiececheck=0;
	char tmpBoard[7][7],tmpBoard1[7][7],tmpBoard2[7][7],tmpBoard3[7][7];
	if(player == 2){
		for(i=0;i<7;i++){
			for(j=0;j<7;j++){
				if(board[i][j] == 'X'){
					int moves1=0,moves2=0,moves3=0,moves4=0;
					pieces--;
					firstO++;
					if(j != 0 && board[i][j-1] == '-'){
						memcpy(tmpBoard, board, 7*7*sizeof(char));
						tmpBoard[i][j-1] = 'X';
						tmpBoard[i][j] = '-';
						moves1=totalmoveX(tmpBoard);
							    									
					}
					if(i != 6 && board[i+1][j] == '-'){
						memcpy(tmpBoard1, board, 7*7*sizeof(char));
						tmpBoard1[i+1][j] = 'X';
						tmpBoard1[i][j] = '-';
						moves2=totalmoveX(tmpBoard1);
							
					}
					if(j != 6 && board[i][j+1] == '-'){
						memcpy(tmpBoard2, board, 7*7*sizeof(char));
						tmpBoard2[i][j+1] = 'X';
						tmpBoard2[i][j] = '-';
						moves3=totalmoveX(tmpBoard2);
								
					}
					if(i != 0 && board[i-1][j] == '-'){
						memcpy(tmpBoard3, board, 7*7*sizeof(char));
						tmpBoard3[i-1][j] = 'X';
						tmpBoard3[i][j] = '-';
						moves4=totalmoveX(tmpBoard3);
					
						}
						a[0]=moves1;
						a[1]=moves2;
						a[2]=moves3;
						a[3]=moves4;
					
						for(int n=0;n<4;n++)
						{
							if((max)>(a[n]))
							{ 
							
							}
							else
							{
								max = (a[n]); 
							
							}	
						}
						if(firstO==d && cond==0){                                      //gets first++ tokens max move value
							d++;
							bestmax=max;
							max=bestmax;              								//searching for the best move for all 0 tokens
						}	
						bestmax=max;
						if(cond==1){    
						                               //if cant find max move on first one checks for second
							if(bestmax==a[0]){
								memcpy(board, tmpBoard, 7*7*sizeof(char));
								printf("\n***** AI moved %dth X piece to left*****\n",firstO);
							
								cond++;
								break;
							}
							else if(bestmax==a[1]){
								memcpy(board, tmpBoard1, 7*7*sizeof(char));
								printf("\n***** AI moved %dth X piece to down*****\n",firstO);
							
								cond++;
								break;
							}
							else if(bestmax==a[2]){
								memcpy(board, tmpBoard2, 7*7*sizeof(char));
								printf("\n***** AI moved %dth X piece to right*****\n",firstO);
							
								cond++;
								break;
							}
							else if(bestmax==a[3]){
								memcpy(board, tmpBoard3, 7*7*sizeof(char));
								printf("\n***** AI moved %dth X piece to up*****\n",firstO);
							
								cond++;
								break;
							}
							
						}	
					}
				}
			}
			if(max==a[0] && cond==0){
				memcpy(board, tmpBoard, 7*7*sizeof(char));
				printf("\n***** AI moved %dth X piece to left*****\n",firstO);
			
				numpiececheck=1;
			}
			else if(max==a[1] && cond==0){
				memcpy(board, tmpBoard1, 7*7*sizeof(char));
				printf("\n***** AI moved %dth X piece to down*****\n",firstO);
		
				numpiececheck=1;
			}
			else if(max==a[2] && cond==0){
				memcpy(board, tmpBoard2, 7*7*sizeof(char));
				printf("\n***** AI moved %dth X piece to right*****\n",firstO);
			
				numpiececheck=1;
			}
			else if(max==a[3] && cond==0){
				memcpy(board, tmpBoard3, 7*7*sizeof(char));
				printf("\n***** AI moved %dth X piece to up*****\n",firstO);
			
				numpiececheck=1;
			}
			else if(pieces==0 && numpiececheck==0){
				int r=aiX(board, 2, pieces, max,cond+1);                //++condt
				return r;
			}	
			
		}
}
int totalmoveO(char board[7][7]){
	int i,j;
	int totalmove = 0;
	for(i=0;i<7;i++){
		for(j=0;j<7;j++){
			if(board[i][j] == 'O'){
				if((j != 0) && board[i][j-1] == '-'){
					totalmove++;
				}
				if((i != 6) && board[i+1][j] == '-'){
					totalmove++;
				}
				if((j != 6) && board[i][j+1] == '-'){
					totalmove++;
				}
				if((i != 0) && board[i-1][j] == '-'){
					totalmove++;
				}
			}
		}
	}
	return totalmove;
}
int totalmoveX(char board[7][7]){
	int i,j;
	int totalmove = 0;
	for(i=0;i<7;i++){
		for(j=0;j<7;j++){
			if(board[i][j] == 'X'){
				if((j != 0) && board[i][j-1] == '-'){
					totalmove++;
				}
				if((i != 6) && board[i+1][j] == '-'){
					totalmove++;
				}
				if((j != 6) && board[i][j+1] == '-'){
					totalmove++;
				}
				if((i != 0) && board[i-1][j] == '-'){
					totalmove++;
				}
			}
		}
	}
	return totalmove;
}
void move(char board[7][7], int player, int turn){
	int X,Y,X2,Y2,tmpX,tmpY;
	int freeSpace = 0,avaliable = 0;;
	char first[100],second[100],Pieces;

	printf("\nChoose piece to move  \n");
	scanf("%s", first);
	printf("Choose the new position for %s = ",first);
	scanf("%s", second);

	
	if(strcmp(first, "a1") == 0){Y = 0; X = 0;}	
		if(strcmp(first, "A1") == 0){Y = 0; X = 0;}
	if(strcmp(first, "a2") == 0){Y = 1; X = 0;}
		if(strcmp(first, "A2") == 0){Y = 1; X = 0;}
	if(strcmp(first, "a3") == 0){Y = 2; X = 0;}
		if(strcmp(first, "A3") == 0){Y = 2; X = 0;}
	if(strcmp(first, "a4") == 0){Y = 3; X = 0;}
		if(strcmp(first, "A4") == 0){Y = 3; X = 0;}
	if(strcmp(first, "a5") == 0){Y = 4; X = 0;}
		if(strcmp(first, "A5") == 0){Y = 4; X = 0;}
	if(strcmp(first, "a6") == 0){Y = 5; X = 0;}
		if(strcmp(first, "A6") == 0){Y = 5; X = 0;}
	if(strcmp(first, "a7") == 0){Y = 6; X = 0;}
		if(strcmp(first, "A7") == 0){Y = 6; X = 0;}
	if(strcmp(first, "b1") == 0){Y = 0; X = 1;}
		if(strcmp(first, "B1") == 0){Y = 0; X = 1;}
	if(strcmp(first, "b2") == 0){Y = 1; X = 1;}
		if(strcmp(first, "B2") == 0){Y = 1; X = 1;}
	if(strcmp(first, "b3") == 0){Y = 2; X = 1;}
		if(strcmp(first, "B3") == 0){Y = 2; X = 1;}
	if(strcmp(first, "b4") == 0){Y = 3; X = 1;}
		if(strcmp(first, "B4") == 0){Y = 3; X = 1;}
	if(strcmp(first, "b5") == 0){Y = 4; X = 1;}
		if(strcmp(first, "B5") == 0){Y = 4; X = 1;}
	if(strcmp(first, "b6") == 0){Y = 5; X = 1;}
		if(strcmp(first, "B6") == 0){Y = 5; X = 1;}
	if(strcmp(first, "b7") == 0){Y = 6; X = 1;}
		if(strcmp(first, "B7") == 0){Y = 6; X = 1;}
	if(strcmp(first, "c1") == 0){Y = 0; X = 2;}
		if(strcmp(first, "C1") == 0){Y = 0; X = 2;}
	if(strcmp(first, "c2") == 0){Y = 1; X = 2;}
		if(strcmp(first, "C2") == 0){Y = 1; X = 2;}
	if(strcmp(first, "c3") == 0){Y = 2; X = 2;}
		if(strcmp(first, "C3") == 0){Y = 2; X = 2;}
	if(strcmp(first, "c4") == 0){Y = 3; X = 2;}
		if(strcmp(first, "C4") == 0){Y = 3; X = 2;}
	if(strcmp(first, "c5") == 0){Y = 4; X = 2;}
		if(strcmp(first, "C5") == 0){Y = 4; X = 2;}
	if(strcmp(first, "c6") == 0){Y = 5; X = 2;}
		if(strcmp(first, "C6") == 0){Y = 5; X = 2;}
	if(strcmp(first, "c7") == 0){Y = 6; X = 2;}
		if(strcmp(first, "C7") == 0){Y = 6; X = 2;}
	if(strcmp(first, "d1") == 0){Y = 0; X = 3;}
		if(strcmp(first, "D1") == 0){Y = 0; X = 3;}
	if(strcmp(first, "d2") == 0){Y = 1; X = 3;}
		if(strcmp(first, "D2") == 0){Y = 1; X = 3;}
	if(strcmp(first, "d3") == 0){Y = 2; X = 3;}
		if(strcmp(first, "D3") == 0){Y = 2; X = 3;}
	if(strcmp(first, "d4") == 0){Y = 3; X = 3;}
		if(strcmp(first, "D4") == 0){Y = 3; X = 3;}
	if(strcmp(first, "d5") == 0){Y = 4; X = 3;}
		if(strcmp(first, "D5") == 0){Y = 4; X = 3;}
	if(strcmp(first, "d6") == 0){Y = 5; X = 3;}
		if(strcmp(first, "D6") == 0){Y = 5; X = 3;}
	if(strcmp(first, "d7") == 0){Y = 6; X = 3;}
		if(strcmp(first, "D7") == 0){Y = 6; X = 3;}
	if(strcmp(first, "e1") == 0){Y = 0; X = 4;}
		if(strcmp(first, "E1") == 0){Y = 0; X = 4;}
	if(strcmp(first, "e2") == 0){Y = 1; X = 4;}
		if(strcmp(first, "E2") == 0){Y = 1; X = 4;}
	if(strcmp(first, "e3") == 0){Y = 2; X = 4;}
		if(strcmp(first, "E3") == 0){Y = 2; X = 4;}
	if(strcmp(first, "e4") == 0){Y = 3; X = 4;}
		if(strcmp(first, "E4") == 0){Y = 3; X = 4;}
	if(strcmp(first, "e5") == 0){Y = 4; X = 4;}
		if(strcmp(first, "E5") == 0){Y = 4; X = 4;}
	if(strcmp(first, "e6") == 0){Y = 5; X = 4;}
		if(strcmp(first, "E6") == 0){Y = 5; X = 4;}
	if(strcmp(first, "e7") == 0){Y = 6; X = 4;}
		if(strcmp(first, "E7") == 0){Y = 6; X = 4;}
	if(strcmp(first, "f1") == 0){Y = 0; X = 5;}
		if(strcmp(first, "F1") == 0){Y = 0; X = 5;}
	if(strcmp(first, "f2") == 0){Y = 1; X = 5;}
		if(strcmp(first, "F2") == 0){Y = 1; X = 5;}
	if(strcmp(first, "f3") == 0){Y = 2; X = 5;}
		if(strcmp(first, "F3") == 0){Y = 2; X = 5;}
	if(strcmp(first, "f4") == 0){Y = 3; X = 5;}
		if(strcmp(first, "F4") == 0){Y = 3; X = 5;}
	if(strcmp(first, "f5") == 0){Y = 4; X = 5;}
		if(strcmp(first, "F5") == 0){Y = 4; X = 5;}
	if(strcmp(first, "f6") == 0){Y = 5; X = 5;}
		if(strcmp(first, "F6") == 0){Y = 5; X = 5;}
	if(strcmp(first, "f7") == 0){Y = 6; X = 5;}
		if(strcmp(first, "F7") == 0){Y = 6; X = 5;}
	if(strcmp(first, "g1") == 0){Y = 0; X = 6;}
		if(strcmp(first, "G1") == 0){Y = 0; X = 6;}
	if(strcmp(first, "g2") == 0){Y = 1; X = 6;}
		if(strcmp(first, "G2") == 0){Y = 1; X = 6;}
	if(strcmp(first, "g3") == 0){Y = 2; X = 6;}
		if(strcmp(first, "G3") == 0){Y = 2; X = 6;}
	if(strcmp(first, "g4") == 0){Y = 3; X = 6;}
		if(strcmp(first, "G4") == 0){Y = 3; X = 6;}
	if(strcmp(first, "g5") == 0){Y = 4; X = 6;}
		if(strcmp(first, "G5") == 0){Y = 4; X = 6;}
	if(strcmp(first, "g6") == 0){Y = 5; X = 6;}
		if(strcmp(first, "G6") == 0){Y = 5; X = 6;}
	if(strcmp(first, "g7") == 0){Y = 6; X = 6;}
		if(strcmp(first, "G7") == 0){Y = 6; X = 6;}
	
	if(player == 1){
		if(board[X][Y] == 'X'){
			Pieces = 'X';
		}
	}
	else if(player == 2){
		if(board[X][Y] == 'O'){
			Pieces = 'O';
		}
	}
	tmpX = X;
	tmpY = Y;
	
	if(strcmp(second, "a1") == 0){Y = 0; X = 0;}
		if(strcmp(second, "A1") == 0){Y = 0; X = 0;}
	if(strcmp(second, "a2") == 0){Y = 1; X = 0;}
		if(strcmp(second, "A2") == 0){Y = 1; X = 0;}
	if(strcmp(second, "a3") == 0){Y = 2; X = 0;}
		if(strcmp(second, "A3") == 0){Y = 2; X = 0;}
	if(strcmp(second, "a4") == 0){Y = 3; X = 0;}
		if(strcmp(second, "A4") == 0){Y = 3; X = 0;}
	if(strcmp(second, "a5") == 0){Y = 4; X = 0;}
		if(strcmp(second, "A5") == 0){Y = 4; X = 0;}
	if(strcmp(second, "a6") == 0){Y = 5; X = 0;}
		if(strcmp(second, "A6") == 0){Y = 5; X = 0;}
	if(strcmp(second, "a7") == 0){Y = 6; X = 0;}
		if(strcmp(second, "A7") == 0){Y = 6; X = 0;}
	if(strcmp(second, "b1") == 0){Y = 0; X = 1;}
		if(strcmp(second, "B1") == 0){Y = 0; X = 1;}
	if(strcmp(second, "b2") == 0){Y = 1; X = 1;}
		if(strcmp(second, "B2") == 0){Y = 1; X = 1;}
	if(strcmp(second, "b3") == 0){Y = 2; X = 1;}
		if(strcmp(second, "B3") == 0){Y = 2; X = 1;}
	if(strcmp(second, "b4") == 0){Y = 3; X = 1;}
		if(strcmp(second, "B4") == 0){Y = 3; X = 1;}
	if(strcmp(second, "b5") == 0){Y = 4; X = 1;}
		if(strcmp(second, "B5") == 0){Y = 4; X = 1;}
	if(strcmp(second, "b6") == 0){Y = 5; X = 1;}
		if(strcmp(second, "B6") == 0){Y = 5; X = 1;}
	if(strcmp(second, "b7") == 0){Y = 6; X = 1;}
		if(strcmp(second, "B7") == 0){Y = 6; X = 1;}
	if(strcmp(second, "c1") == 0){Y = 0; X = 2;}
		if(strcmp(second, "C1") == 0){Y = 0; X = 2;}
	if(strcmp(second, "c2") == 0){Y = 1; X = 2;}
		if(strcmp(second, "C2") == 0){Y = 1; X = 2;}
	if(strcmp(second, "c3") == 0){Y = 2; X = 2;}
		if(strcmp(second, "C3") == 0){Y = 2; X = 2;}
	if(strcmp(second, "c4") == 0){Y = 3; X = 2;}
		if(strcmp(second, "C4") == 0){Y = 3; X = 2;}
	if(strcmp(second, "c5") == 0){Y = 4; X = 2;}
		if(strcmp(second, "C5") == 0){Y = 4; X = 2;}
	if(strcmp(second, "c6") == 0){Y = 5; X = 2;}
		if(strcmp(second, "C6") == 0){Y = 5; X = 2;}
	if(strcmp(second, "c7") == 0){Y = 6; X = 2;}
		if(strcmp(second, "C7") == 0){Y = 6; X = 2;}
	if(strcmp(second, "d1") == 0){Y = 0; X = 3;}
		if(strcmp(second, "D1") == 0){Y = 0; X = 3;}
	if(strcmp(second, "d2") == 0){Y = 1; X = 3;}
		if(strcmp(second, "D2") == 0){Y = 1; X = 3;}
	if(strcmp(second, "d3") == 0){Y = 2; X = 3;}
		if(strcmp(second, "D3") == 0){Y = 2; X = 3;}
	if(strcmp(second, "d4") == 0){Y = 3; X = 3;}
		if(strcmp(second, "D4") == 0){Y = 3; X = 3;}
	if(strcmp(second, "d5") == 0){Y = 4; X = 3;}
		if(strcmp(second, "D5") == 0){Y = 4; X = 3;}
	if(strcmp(second, "d6") == 0){Y = 5; X = 3;}
		if(strcmp(second, "D6") == 0){Y = 5; X = 3;}
	if(strcmp(second, "d7") == 0){Y = 6; X = 3;}
		if(strcmp(second, "D7") == 0){Y = 6; X = 3;}
	if(strcmp(second, "e1") == 0){Y = 0; X = 4;}
		if(strcmp(second, "E1") == 0){Y = 0; X = 4;}
	if(strcmp(second, "e2") == 0){Y = 1; X = 4;}
		if(strcmp(second, "E2") == 0){Y = 1; X = 4;}
	if(strcmp(second, "e3") == 0){Y = 2; X = 4;}
		if(strcmp(second, "E3") == 0){Y = 2; X = 4;}
	if(strcmp(second, "e4") == 0){Y = 3; X = 4;}
		if(strcmp(second, "E4") == 0){Y = 3; X = 4;}
	if(strcmp(second, "e5") == 0){Y = 4; X = 4;}
		if(strcmp(second, "E5") == 0){Y = 4; X = 4;}
	if(strcmp(second, "e6") == 0){Y = 5; X = 4;}
		if(strcmp(second, "E6") == 0){Y = 5; X = 4;}
	if(strcmp(second, "e7") == 0){Y = 6; X = 4;}
		if(strcmp(second, "E7") == 0){Y = 6; X = 4;}
	if(strcmp(second, "f1") == 0){Y = 0; X = 5;}
		if(strcmp(second, "F1") == 0){Y = 0; X = 5;}
	if(strcmp(second, "f2") == 0){Y = 1; X = 5;}
		if(strcmp(second, "F2") == 0){Y = 1; X = 5;}
	if(strcmp(second, "f3") == 0){Y = 2; X = 5;}
		if(strcmp(second, "F3") == 0){Y = 2; X = 5;}
	if(strcmp(second, "f4") == 0){Y = 3; X = 5;}
		if(strcmp(second, "F4") == 0){Y = 3; X = 5;}
	if(strcmp(second, "f5") == 0){Y = 4; X = 5;}
		if(strcmp(second, "F5") == 0){Y = 4; X = 5;}
	if(strcmp(second, "f6") == 0){Y = 5; X = 5;}
		if(strcmp(second, "F6") == 0){Y = 5; X = 5;}
	if(strcmp(second, "f7") == 0){Y = 6; X = 5;}
		if(strcmp(second, "F7") == 0){Y = 6; X = 5;}
	if(strcmp(second, "g1") == 0){Y = 0; X = 6;}
		if(strcmp(second, "G1") == 0){Y = 0; X = 6;}
	if(strcmp(second, "g2") == 0){Y = 1; X = 6;}
		if(strcmp(second, "G2") == 0){Y = 1; X = 6;}
	if(strcmp(second, "g3") == 0){Y = 2; X = 6;}
		if(strcmp(second, "G3") == 0){Y = 2; X = 6;}
	if(strcmp(second, "g4") == 0){Y = 3; X = 6;}
		if(strcmp(second, "G4") == 0){Y = 3; X = 6;}
	if(strcmp(second, "g5") == 0){Y = 4; X = 6;}
		if(strcmp(second, "G5") == 0){Y = 4; X = 6;}
	if(strcmp(second, "g6") == 0){Y = 5; X = 6;}
		if(strcmp(second, "G6") == 0){Y = 5; X = 6;}
	if(strcmp(second, "g7") == 0){Y = 6; X = 6;}
		if(strcmp(second, "G7") == 0){Y = 6; X = 6;}	
	
	X2 = X;
	Y2 = Y;
	X = tmpX;
	Y = tmpY;
	
	if(Y != 0){
		if(X+Y-1 == X2+Y2){			//checks for left move between first place and second place
		avaliable = 1;
		}
	}
	if(X != 6){
		if(X+1+Y == X2+Y2){			//checks for down move between first place and second place
		avaliable = 1;
		}
	}
    if(Y != 6){
		if(X+Y+1 == X2+Y2){			//checks for right move between first place and second place
		avaliable = 1;
		}
	}
	if(X != 0){
		if(X-1+Y == X2+Y2){			//checks for upper move between first place and second place
		avaliable = 1;
		}
	}
	if(board[X2][Y2] == '-'){		//cheks for freespace
		freeSpace = 1;
	}
	if(board[X][Y] == Pieces){					//cheks for users to play own pieces
	
		if(avaliable == 1 && freeSpace == 1){   //if there beteen firs place and second place there is a max 1 move difference and the secon place was empity moves the piece
			if(board[X][Y] == Pieces){				
				board[X2][Y2] = Pieces;
				board[X][Y] = '-';
				turn--;
				printf("\n****	Player moves the piece at %s to %s	****\n", first, second);
			}
		}	
		else{										//otherwise returns same function
			printf("\n*****ERROR*****\n");
			printf("Pieces can only move left-down-rigt-up\n");
			printf("*****PLEASE TRY AGAIN*****\n");
			move(board,player,turn);			//recursive
		}
	}
	else{									
		printf("\n*****ERROR*****\n");
		printf("You have to choose your on piece\n");
		printf("*****PLEASE TRY AGAIN*****\n");
		move(board,player,turn);		
	}
	
}
void getBoard(int pieces, char board[7][7]){
	int i,j,a,rand1,rand2;	
	srand(time(0));
	rand1 = (rand() % 7);
	rand2 = (rand() % 7);
	for(i=0;i<7;i++){
		for(j=0;j<7;j++){
			board[i][j] = '-';
		}
	}
	for(a=0; a<(pieces*2); a++){		
		if(a%2){
			board[rand1][rand2] = 'X';
		}
		else{
			board[rand1][rand2] = 'O';
		}	
		while(board[rand1][rand2] != '-'){
			rand1 = (rand() % 7);
			rand2 = (rand() % 7);
		}		
	}
}
void printBoard(char board[7][7]){
	int i,j;
	int c=0;
	printf("\n  1 2 3 4 5 6 7\n");
	for(i=0;i<7;i++){
			if(c==0){
				printf("a ");
			}
			if(c==1){
				printf("b ");
			}
			if(c==2){
				printf("c ");
			}
			if(c==3){
				printf("d ");
			}
			if(c==4){
				printf("e ");
			}
			if(c==5){
				printf("f ");
			}
			if(c==6){
				printf("g ");
			}
		
		for(j=0;j<7;j++){
			printf("%c ", board[i][j]);
		}
		printf("\n");
		c++;
	}
}


