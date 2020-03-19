#include <string.h>
#include <stdio.h>
#include <stdlib.h>

void printSpaces(int n)
{
	for (int i = 0; i < n; i++) {
		printf(" ");
	}
}

int cntPos(int n)
{
	int f = n;
	int ret = 0;

	for (n = f; n > 0; n /= 10, ret++);
	return ret;
}

int main()
 {
	int z , left, len1, len2, t, i, j, p;
	char number1[256];
	char number2[256 ];

	do{
	  t=0, p=0;
	  printf("Vvefite pervoe celoe chislo:\n ");
	  scanf("%s", number1);
	  len1 = strlen(number1);
	  for (i = 0 ; i < len1; i++) {
		  if (number1[i] < 48 || number1[i] > 57) {  //проверка на ввод 1 числа
			 t = 1;
		  }
	  }

	  if (t == 0) {
	  printf("Vvedite vtoroe celoe chislo:\n ");
	  scanf("%s", number2);
	  len2 = strlen(number2);
	  for (j = 0; j < len2; j++) {
		  if (number2[j] < 48 || number2[j] > 57) {    //проверка на ввод 2 числа
			 p = 1;
		  }
	  }
	  if (p == 0) {


	  if (len1 > len2) {
		 left = len2;
	  }
			else {
			   left = len1;
			}

	  int diff = len1 - len2;

	  if (diff < 0) {   //если diif=отрицательное
		 diff *= -1;
	  }
	  left += 1;
	  printSpaces(left);

	  int start = len1 + len2 + 1;
	  int oldstart = start;

	  if (len1 < len2) { //чтобы второе число не заходило на знак *
		 printSpaces(diff);
	  }
	  printf("%s", number1);
	  printf("*\n");
	  printSpaces(left);
	  if (len1 > len2) {  //чтобы второе число не заходило на знак*
		 printSpaces(diff);
	  }
	  printf("%s", number2);
	  printf("\n");
	  printSpaces(left);
	  for (z = left; z < start; z++) {
		  printf("_");
	  }

	  int fnumber = atoi(number1);
	  int snumber = atoi(number2);
	  int answer = fnumber * snumber;

	  for (int i = strlen(number2) - 1; i > -1; i--) {
		  printf("\n");

		  int curnum = number2[i] - 48;  //перевод из символьного в числовой
		  int res = curnum * fnumber;

		  printSpaces(start - cntPos(res));
		  printf("%i", res);
		  if (i > 0) {
			 printf("+");
		  }
		  start--;
	  }
	  printf("\n");
	  left = oldstart - cntPos(answer);
	  printSpaces(left);
	  for (z = left; z < oldstart; z++) {
		  printf("_");
	  }
	  printf("\n");
	  printSpaces(left);
	  printf("%i", answer);
	  scanf("%d", &z);
	  }
	  }
	  }
	  while (t==1 || p==1);
	  return 0;

}
