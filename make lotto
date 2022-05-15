#include<stdio.h>
#include<stdlib.h>
#include<time.h>

void generate_lotto(int *plotto); //로또 번호를 생성하는 함수
int has_number(const int *plotto, int num); //입력된 num이 plotto가 가리키는 배열에 있으면 1 없으면0 리턴 하는 함수
void print_lotto(const int lotto[]); //로또 배열을 출력하는 함수
void sort(int list[]); //로또 배열 정렬

int main(){
	int list[6], n, i;           //지역변수 선언
	srand((unsigned)time(NULL)); //rand함수에 사용될 수를 초기화
	while(1){                    //무한루프를 통해 중복된 수가 나오면 다시 계속 반복
		generate_lotto(list);    //로또 번호 생성
		i = 0;                   //무한루프의 지속여부를 결정하는 변수 i를 0으로 초기화
		for (n = 0; n < 6; n++) { 
			if (has_number(list, n) == 1) { //중복이 있으면 i값을 1로 바꾼다음 for문 탈출 후 다시 루프
				i = 1;
				break;
			}
		}
		if (i == 0) break; //중복이 없으면 무한루프 탈출
	}
	sort(list); //로또 번호를 오름차순으로 정렬
	print_lotto(list); //로또 번호 출력
	return 0;
}

void generate_lotto(int *plotto) {
	int i;
	for(i = 0; i < 6; i++)        
	plotto[i] = (rand() % 45) + 1; //반복문을 통해 6개의 배열안에 중복 허용해서 각각 1~45 사이의 수를 입력
}

int has_number(const int *plotto, int num) {
	int i;
	for (i = num+1; i < 6; i++) { //6개의 배열중 서로다른 주소를 갇는 배열끼리 비교
		if (plotto[num] == plotto[i]) { //중복되는 수가 있으면 1을 리턴
			return 1;
			break;
		}
	}
	return 0;  //중복되는 수가 없으면 0을 리턴
}

void print_lotto(const int lotto[]) { 
	int i;
	printf("로또 번호 : ");
	for(i = 0; i < 6; i++)    //6개의 배열에 있는 로또 번호수 출력 
	printf("%d ", lotto[i]);
}

void sort(int list[]) {
	int i, j, tmp, least;

	for (i = 0; i < 5; i++) {//두 배열 값을 비교 후 작은 수를 가린 후 반복문을 통해 끝날때까지 그 다음 배열값과 비교
		least = i;
		for (j = i + 1; j < 6; j++)
			if (list[j] < list[least]) least = j;

		tmp = list[i]; //기존 배열을 오름차순으로 정렬된 배열로 변경
		list[i] = list[least];
		list[least] = tmp;
	}
}
