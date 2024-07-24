#include <stdio.h>
#include <stdlib.h>
#include <signal.h>
#include <locale.h>
#include <unistd.h> // Para a funcao sleep

// Variavel para controlar o loop infinito
int keepRunning = 1;

int expoAtivo1 = 1; 
int expoAtivo2 = 1; 
int expoAtivo3 = 1; 
int expoAtivo4 = 1;

int notaExpo1, notaExpo2, notaExpo3, notaExpo4, notaRecomenda, notaRevisita, expo;
int expoVisu1, expoVisu2, expoVisu3, expoVisu4;

float media1, media2, media3, media4;

// Funcao de tratamento de sinal para Ctrl+C
void intHandler(int dummy) {
    system("cls"); // Use "cls" em sistemas Windows
    fflush(stdout);
    printf("Ctrl+C pressionado. Saindo...\n");
    keepRunning = 0;
}

void questionario(){
	
	int resposta1, recomenda, revisita;
	
	printf("1 - Qual nota voce daria para esta exposicao de 1 a 5? ");
	scanf("%d", &resposta1);
	printf("2 - Em uma escala de 1 a 5, quanto voce recomendaria nosso museu para um amigo ou familiar?");
	scanf("%d", &recomenda);
	printf("3 - Voce retornaria para o nosso museu? (1 - Sim | 2 - Nao )");
	scanf("%d", &revisita);

	
	if (expo == 1){
		notaExpo1 += resposta1;
		expoVisu1++;
		media1 = (notaExpo1 / expoVisu1);
	} else if (expo == 2){
		notaExpo2 += resposta1;
		expoVisu2++;
		media2 = (notaExpo2 / expoVisu2);
	} else if (expo == 3){
		notaExpo3 += resposta1;
		expoVisu3++;
		media3 = (notaExpo3 / expoVisu3);
	} else if (expo == 4){
		notaExpo4 += resposta1;
		expoVisu4++;
		media4 = (notaExpo4 / expoVisu4);
	}
	
	notaRevisita += revisita;
	notaRecomenda += recomenda;
	
	printf("\nPressione Enter para continuar...");
	getchar();
    getchar();
    system("cls");	

}

void exposicoes (){
	
	// Decisao se a exposicao deve continuar?
    if (expoAtivo1 > 0) {
        printf("1 - 100 Anos da Semana de Arte Moderna\n");
    }
    
    if (expoAtivo2 > 0) {
        printf("2 - 150 Anos de Santos Dumont\n");
    }

    if (expoAtivo3 > 0) {
        printf("3 - Jogos Olimpicos de Paris 2024\n");
    }

    if (expoAtivo4 > 0) {
        printf("4 - Exposicao de Van Gogh\n");
    }
	
}



int main(void){
    setlocale(LC_ALL, "Portuguese");
	
	char exposicao;
	int confirmacao, remocao;
	
// Registra o tratador de sinal para Ctrl+C
	signal(SIGINT, intHandler);
	
	while (keepRunning) {
		system("cls"); // Use "cls" em sistemas Windows
		printf("Bem vindo(a) ao Museu Multitematico da Era Digital!\n\n");
		printf("Digite o numero da exposicao que voce deseja ver:\n");
		exposicoes();
		scanf("%c", &exposicao);
		system("cls");
		
		switch(exposicao)
		{
		    case '1':
		    	printf("100 ANOS DA ARTE MODERNA\n\n");
		    	printf("Artistas reuniram-se em fevereiro de 1922 e um evento que gerou uma renovacao intelectual e artistica no Brasil.\n");
		    	printf("O evento reuniu diversas apresentacoes de danca, musica, recital de poesias, exposicao de obras - pintura e escultura - e palestras.\n"); 
				printf("Os artistas envolvidos propunham uma nova visao de arte, a partir de uma estetica inovadora inspirada nas vanguardas europeias.\n");
				printf("Juntos, eles buscavam uma renovacao social e artistica no pais, evidenciada na 'Semana de 22'.\n");
				printf("O evento chocou parte da populacao e trouxe a tona uma nova visao sobre os processos artisticos, bem como a apresentacao de uma arte mais brasileira.\n\n");
                
				// Obra 1
				printf("1o Obra \n");
				printf("O Homem Amarelo e uma famosa pintura de Anita Malfatti, que fez parte de exposicoes importantes no Brasil.\n"); 
				printf("A obra retrata um homem pobre e desconhecido, possivelmente um imigrante italiano, com um olhar melancolico e desesperado.\n");
				printf("Apesar de estar vestido com um terno, seu paleto esta desgastado, e a imagem dele parece se estender alem da tela, uma caracteristica tipica das obras de Malfatti.\n");
				printf("Os olhos do homem sao marcados por contornos escuros e sobrancelhas acentuadas.\n");
				printf("A pintura teve uma versao anterior nos Estados Unidos, enquanto Anita estudava, mas a segunda versao e a mais conhecida.\n\n");
				
				// Obra 2
				printf("2o Obra \n");
				printf("A pintura 'Pierrete' de Di Cavalcanti, criada em 1922, retrata uma moca vestida ao estilo 'pierrot' para o carnaval.\n");
				printf("Esta obra pertence ao primeiro periodo modernista e foi criada com tinta a oleo, medindo 78 x 65 cm.\n");
				printf("A atmosfera lirica e notavel na figura feminina, que parece estar dancando suavemente, com passaros voando em sua direcao e um vaso de flores no canto direito, criando um ambiente poetico e delicado.\n\n");
				
				printf("Pressione Enter para continuar...");
                getchar();
                getchar();
                system("cls");
                expo = 1;
				questionario(); // Preenche as respostas do usuario

            break;
				
		    case '2':
		    	printf("150 ANOS DE SANTOS DUMONT\n\n");
				printf("Alberto Santos Dumont foi um aeronauta, esportista, autodidata e inventor brasileiro.\n");
				printf("Dumont e amplamente reconhecido como o pai da aviacao, tendo realizado o primeiro voo homologado da historia.\n");
				printf("Santos Dumont projetou, construiu e voou os primeiros baloes dirigiveis com motor a gasolina.\n\n");
                
                // Obra 1 
                printf("1o Obra \n");
                printf("O 14 BIS tem capacidade para um tripulante.\n");
                printf("Foi o primeiro aviao mais pesado que o ar a conseguir decolar por seus proprios meios.\n");
                printf("Esse fato historico teve lugar em Bagatelle (centro de Paris), no dia 23 de outubro de 1906.\n");
                printf("Nessa data, Santos Dumont decolou com seu 14 BIS e percorreu 60 metros em 7 segundos, voando a uma altura de 2 metros do solo,\n");
                printf("perante mais de mil espectadores e da Comissao Oficial do Aeroclube da Franca, que era uma instituicao de reconhecimento internacional e autorizada a homologar qualquer descoberta aeronautica marcante,\n");
                printf("tanto no campo dos aerostatos (veiculos mais leves que o ar), como no dos aerodinos (veiculos mais pesados que o ar).\n\n");
		    		
				printf("Pressione Enter para continuar...");
                getchar();
                getchar();
                system("cls");
                expo = 2;
                questionario();
			break;
			
		    
		    case '3':
		    	printf("JOGOS OLIMPICOS DE PARIS 2024\n\n");
		    	printf("Os Jogos Olimpicos de 2024, oficialmente conhecidos como Paris 2024, serao realizados na cidade de Paris, Franca, no segundo semestre de 2024.\n");
		    	printf("Esta sera a terceira vez que Paris sediara os Jogos Olimpicos, apos as edicoes de 1900 e 1924.\n");
		    	printf("A Franca ja foi anfitria de seis edicoes dos Jogos Olimpicos, incluindo os Jogos de Inverno.\n");
		    	printf("Paris 2024 representa a primeira edicao fora do Extremo Oriente em seis anos e a primeira na Uniao Europeia em doze anos.\n");
		    	printf("Paris venceu a candidatura para sediar os Jogos, competindo com Los Angeles.\n\n");
		    	
				// Obra 1
				printf("O Breaking fara sua estreia nos Jogos Olimpicos em Paris 2024, com competicoes separadas para homens e mulheres.\n");
				printf("Cada evento contara com 16 B-Boys e 16 B-Girls competindo em batalhas individuais, usando movimentos de danca e improvisacao ao ritmo de faixas de DJ.\n");
				printf("O Breaking foi introduzido nos Jogos Olimpicos da Juventude em Buenos Aires em 2018.\n\n");
				
				printf("Pressione Enter para continuar...");
                getchar();
                getchar();
                system("cls");
                expo = 3;
                questionario();
			break;
		    
		    case '4':
		    	printf("EXPOSIÇÃO DE VAN GOGH\n\n");
		    	printf("Vincent van Gogh foi um famoso pintor pos-impressionista holandes do seculo XIX, conhecido por sua obra marcante e intensa.\n");
		    	printf("Van Gogh e reconhecido por seu estilo unico, marcado por pinceladas ousadas e cores vibrantes, e por sua luta contra problemas de saude mental ao longo de sua vida.\n");
		    	printf("Sua contribuicao para a arte e altamente valorizada, e ele e considerado um dos grandes mestres da pintura.\n\n");
		    	
				// Obra 1
		    	printf("1o Obra \n");
				printf("O quadro mais famoso do pintor holandes foi criado enquanto Van Gogh estava internado no hospital psiquiatrico de Saint-Remy-de-Provence durante o ano de 1889.\n");
		    	printf("A tela 'A Noite Estrelada (1889)' ilustra o nascer do sol visto da janela do quarto onde Van Gogh dormia. \n");
		    	printf("O trabalho apresenta alguns elementos peculiares como as espirais do ceu que imprimem uma nocao de profundidade e movimento.\n");
		    	printf("Apesar do ceu caotico, o vilarejo que aparece na pintura tem ar pacato e alheio ao turbilhao exterior.\n\n");
		    	
				// Obra 2
				printf("2o Obra \n");
				printf("A tela 'Os Girassois (1889)' Uma das obras-primas do pintor holandes, a tela que tem como protagonista um vaso de girassois tem dez versoes.\n");
		    	printf("Na imagem vemos a preponderancia do amarelo e uma organizacao das flores nada convencional.\n");
				printf("A pintura do holandes apresenta confusao, caos e uma beleza perturbadora obtida com os girassois retorcidos.\n\n");
				
				// Obra 3
				printf("3o Obra \n");
		    	printf("O 'Autorretrato com a orelha cortada (1889)'.\n");
		    	printf("A amputacao da orelha direita foi um episodio nebuloso na vida do pintor que ainda hoje permanece misterioso.\n");
		    	printf("Sabemos apenas que a perda da orelha foi resultado direto de uma violenta discussao que teve com o amigo tambem pintor Paul Gauguin em 1888.\n");
		    	printf("Gauguin havia se mudado para a residencia artistica de Van Gogh no mesmo ano, a convite do amigo.\n\n");

				printf("Pressione Enter para continuar...");
                getchar();
                getchar();
                system("cls");
                expo = 4;
                questionario();
		    break;
		    
		    case '9':
		    	// Relatorio
			    system("cls"); // Use "cls" em sistemas Windows
			    printf("Relatorio das notas:\n");
			    printf("1 - Nota para a exposicao 1: %d\n", notaExpo1);
			    printf("2 - Nota para a exposicao 2: %d\n", notaExpo2);
			    printf("3 - Nota para a exposicao 3: %d\n", notaExpo3);
			    printf("4 - Nota para a exposicao 4: %d\n", notaExpo4);
			    printf("5 - Recomendacao do museu: %d\n", notaRecomenda);
			    printf("6 - Retorno ao museu: %d\n", notaRevisita);

				// Decisao se a exposicao deve continuar?
				if ((expoVisu1 > 0) && (media1 < 3.0)) {
				    printf("\n A exposicao '100 Anos da Semana de Arte Moderna' esta com media de %.2f\n", media1);
				    printf("Deseja remover a exposicao? (1 - Sim | 2 - Nao ): ");
				    scanf("%d", &remocao);
				    if (remocao == 1) {
				        // Aqui voce pode adicionar a logica para remover a exposicao
				        expoAtivo1 = 0;
				        printf("Exposicao '100 Anos da Semana de Arte Moderna' removida do catalogo.\n");
				    }
				}
				if ((expoVisu2 > 0) && (media2 < 3.0)) {
				    printf("\n A exposicao '150 Anos de Santos Dumont' esta com media de %.2f\n", media2);
				    printf("Deseja remover a exposicao? (1 - Sim | 2 - Nao ): ");
				    scanf("%d", &remocao);
				    if (remocao == 1) {
				        // Aqui voce pode adicionar a logica para remover a exposicao
				        expoAtivo2 = 0;
				        printf("Exposicao '150 Anos de Santos Dumont' removida do catalogo.\n");
				    }
				}
				if ((expoVisu3 > 0) && (media3 < 3.0)) {
				    printf("\n A exposicao 'Jogos Olimpicos de Paris 2024' esta com media de %.2f\n", media3);
				    printf("Deseja remover a exposicao? (1 - Sim | 2 - Nao ): ");
				    scanf("%d", &remocao);
				    if (remocao == 1) {
				        // Aqui voce pode adicionar a logica para remover a exposicao
				        expoAtivo3 = 0;
				        printf("Exposicao 'Jogos Olimpicos de Paris 2024' removida do catalogo.\n");
				    }
				}
				if ((expoVisu4 > 0) && (media4 < 3.0)) {
				    printf("\n A exposicao 'Exposicao de Van Gogh' esta com media de %.2f\n", media4);
				    printf("Deseja remover a exposicao? (1 - Sim | 2 - Nao ): ");
				    scanf("%d", &remocao);
				    if (remocao == 1) {
				        // Aqui voce pode adicionar a logica para remover a exposicao
				        expoAtivo4 = 0;
				        printf("Exposicao 'Exposicao de Van Gogh' removida do catalogo.\n");
				    }
				}
				
				printf("\nPressione Enter para continuar...");
				getchar();
			    getchar();
			    system("cls");
		    break;
		    
		    case '-':
		    	printf("Tem certeza que seja encerrar a aplicacao? (1 - Sim | 2 - Nao )");
		    	scanf("%d", &confirmacao);
		    	
		    	if (confirmacao == 1){
		    		printf("Encerrando...");
                	getchar();
                	system("cls");
					keepRunning = 0;		
				} else if (confirmacao == 2) {
					printf("Ok!");
				    getchar();
					system("cls");	
				}
		    break;
		    
		    case 'a':
		    	
		    	// Decisao se a exposicao deve continuar?
		    	
		    	if ((expoAtivo1 == 1) && (expoAtivo2 == 1) && (expoAtivo3 == 1) && (expoAtivo4 == 1)) {
		    		printf("Nao ha nada para ser reativado");	
					getchar();
					getchar();	
				} else {
					
					if (expoAtivo1 == 0) {
					    printf("\n A exposicao '100 Anos da Semana de Arte Moderna' esta desativada \n");
					    printf("Deseja reativar a exposicao? (1 - Sim | 2 - Nao ): ");
					    scanf("%d", &remocao);
					    if (remocao == 1) {
					        // Aqui voce pode adicionar a logica para remover a exposicao
					        expoAtivo1 = 1;
					        printf("Exposicao '100 Anos da Semana de Arte Moderna' foi adicionada ao catalogo.\n");
					        getchar();
					        getchar();
					    }
					}  
					if (expoAtivo2 == 0) {
					    printf("\n A exposicao '150 Anos de Santos Dumont' esta desativada \n");
					    printf("Deseja reativar a exposicao? (1 - Sim | 2 - Nao ): ");
					    scanf("%d", &remocao);
					    if (remocao == 1) {
					        // Aqui voce pode adicionar a logica para remover a exposicao
					        expoAtivo2 = 1;
					        printf("Exposicao '150 Anos de Santos Dumont' foi adicionada ao catalogo.\n");
					        getchar();
					        getchar();
					    }
					} 
					if (expoAtivo3 == 0) {
					    printf("\n A exposicao 'Jogos Olimpicos de Paris 2024' esta desativada \n");
					    printf("Deseja reativar a exposicao? (1 - Sim | 2 - Nao ): ");
					    scanf("%d", &remocao);
					    if (remocao == 1) {
					        // Aqui voce pode adicionar a logica para remover a exposicao
					        expoAtivo3 = 1;
					        printf("Exposicao 'Jogos Olimpicos de Paris 2024' foi adicionada ao catalogo.\n");
					        getchar();
					        getchar();
					    }
					} 
					if (expoAtivo4 == 0) {
					    printf("\n A exposicao 'Exposicao de Van Gogh' esta desativada \n");
					    printf("Deseja reativar a exposicao? (1 - Sim | 2 - Nao ): ");
					    scanf("%d", &remocao);
					    if (remocao == 1) {
					        // Aqui voce pode adicionar a logica para remover a exposicao
					        expoAtivo4 = 1;
					        printf("Exposicao 'Exposicao de Van Gogh' foi adicionada ao catalogo.\n");
					        getchar();
					        getchar();
					    }
					}
				}
		    	
		    break;
		    
		    default: 
		    printf("Opcao invalida\n");
		    
		}
	
	 }
	
	     return 0;
}
