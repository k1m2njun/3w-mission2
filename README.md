#include <stdio.h>
#include <cs50.h>
#include <stdlib.h>
#include <string.h>

const int NUMBER_OF_GRADES = 9;
const int SCORES[NUMBER_OF_GRADES] = {95, 90, 85, 80, 75, 70, 65, 60, 0};
const char *GRADES[NUMBER_OF_GRADES] = {"A+", "A ", "B+", "B ", "C+", "C ", "D+", "D ", "F "};

int main(void) {
    printf("   <학점 계산 프로그램>\n종료를 원하면 '-1'을 입력하세요.");
    printf("\n점수 : ");

    for(int i = 0; i < NUMBER_OF_GRADES; i++) {
        printf("%d     ",SCORES[i]);
    }

    printf("\n학점 : ");

    for(int i = 0; i < NUMBER_OF_GRADES; i++) {
	    printf("%s     ", GRADES[i]);
    }
    
    int cnt = 0;
    
    for(int i = 0; true; i++) {
        float studentAnswer = get_float("\n성적을 입력하세요. (0 ~ 100) : ");
        
        if(studentAnswer == -1) {
                printf("학점프로그램을 종료합니다.\n");
                break;
        }
        else if(studentAnswer > 100 || studentAnswer < 0 ) {
                printf("** %.0f 성적을 올바르게 입력하세요. 범위는 (0 ~ 100) 입니다.\n", studentAnswer);
        }       

        for(int j = 0; j < 10; j++) {
            
            if(SCORES[j] > studentAnswer) {
                cnt++;
            }
            else if(studentAnswer >= SCORES[j]) {
                printf("학점은 %s입니다.",GRADES[cnt]);
                break;
            }
        }

        cnt=0;
    }
}
