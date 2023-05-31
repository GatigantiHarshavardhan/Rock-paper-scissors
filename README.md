#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    int player_choice, computer_choice, num_rounds, round_num, player_score, computer_score;
    srand(time(NULL)); // seed the random number generator

    printf("Welcome to rock-paper-scissors!\n");
    printf("Enter the number of rounds you want to play:\n");

    scanf("%d", &num_rounds);

    if (num_rounds <= 0) {
        printf("Invalid number of rounds, please enter a positive integer\n");
        return 1;
    }

    player_score = 0;
    computer_score = 0;

    for (round_num = 1; round_num <= num_rounds; round_num++) {
        printf("Round %d\n", round_num);
        printf("Enter your choice:\n");
        printf("0 for rock, 1 for paper, 2 for scissors\n");

        scanf("%d", &player_choice);

        if (player_choice < 0 || player_choice > 2) {
            printf("Invalid choice, please enter a number between 0 and 2\n");
            round_num--; // repeat this round
            continue;
        }

        computer_choice = rand() % 3;

        printf("You chose ");
       switch(player_choice) {
            case 0:
                printf("rock\n");
                break;
            case 1:
                printf("paper\n");
                break;
            case 2:
                printf("scissors\n");
                break;
        }

        printf("The computer chose ");
        switch(computer_choice) {
            case 0:
                printf("rock\n");
                break;
            case 1:
                printf("paper\n");
                break;
            case 2:
                printf("scissors\n");
                break;
        }

        if (player_choice == computer_choice) {
            printf("It's a tie!\n");
        } else if (player_choice == 0 && computer_choice == 2 ||
                   player_choice == 1 && computer_choice == 0 ||
                   player_choice == 2 && computer_choice == 1) {
            printf("You win this round!\n");
            player_score++;
        } else {
            printf("The computer wins this round!\n");
            computer_score++;
        }

        printf("Score: You %d, Computer %d\n", player_score, computer_score);
    }

    printf("Game over!\n");

    if (player_score > computer_score) {
        printf("Congratulations, you win!\n");
    } else if (player_score < computer_score) {
        printf("Sorry, the computer wins!\n");
    } else {
        printf("It's a tie!\n");
    }

    return 0;
}

