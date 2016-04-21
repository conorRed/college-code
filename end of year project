#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int readFile();
void compareName(char*,int);
void compareSport(char*, int);
void compareCountry(char*,int);
void results_sport_year(char*,int,int);

struct athlete{
char name[150];
int age,total,bronze,gold,silver,year;
char country[100];
char sport[100];
};
struct athlete athletes[10000];
/*************************************************************************************************************/
int main()
{
    char*name,*sport,*country;
    name = malloc(256);//making space for character pointers
    sport = malloc(256);
    country = malloc(256);
    int i,year;
    i = readFile();
    printf("Please enter athlete:\n");
    gets(name);
    compareName(name,i);
    free(name);// freeing memory
    printf("Enter Sport:\n");
    gets(sport);
    compareSport(sport,i);
    printf("Enter Country:\n");
    gets(country);
    compareCountry(country,i);
    free(country);
    printf("Enter Sport:\n");
    gets(sport);
    printf("Enter Year:\n");
    scanf("%d",&year);
    results_sport_year(sport,year,i);
    free(sport);
    return 0;

}
/*************************************************************************************************************/
int readFile(){
FILE *fptr;
int i;
char *token;
char line[800];
fptr = fopen("olympics.txt", "r");
    if (fptr == NULL)
	{
		printf ("Error");
	}
    i = 0;
    while ((fgets(line,800,fptr) != NULL))// parsing through file taking out info.
	{
        token = strtok(line,"\t");
        strcpy(athletes[i].name, token);

        token = strtok(NULL,"\t");
        athletes[i].age = atoi(token);

        token = strtok(NULL,"\t");
        strcpy(athletes[i].country, token);

        token = strtok(NULL,"\t");
        athletes[i].year = atoi(token);

        token = strtok(NULL,"\t");
        strcpy(athletes[i].sport, token);

        token = strtok(NULL,"\t");
        athletes[i].gold = atoi(token);
        token = strtok(NULL,"\t");
        athletes[i].silver = atoi(token);
        token = strtok(NULL,"\t");
        athletes[i].bronze = atoi(token);
        token = strtok(NULL,"\t");
        athletes[i].total = atoi(token);

i++;// getting number of lines
token = NULL;// initializing token
	}
	fclose(fptr);

    return i;

}
/*************************************************************************************************************/
void compareName(char*name,int i){
    int j,result_found;
    j = 0;
    int temp_a,temp_b,temp_c,temp_d;
    result_found = 0;

for(j = 0; j < i; j++){// if the same person wins on a different year add their medals up
        if(strcasecmp(athletes[j].name,athletes[j+1].name) == 0){
           athletes[j+1].bronze += athletes[j].bronze;
           athletes[j+1].silver += athletes[j].silver;
           athletes[j+1].gold += athletes[j].gold;
           athletes[j+1].total += athletes[j].total;

           }

   if(strcasecmp(athletes[j].name,name) == 0){ //looping through matching names to get medals
    temp_a = athletes[j].bronze;
    temp_b = athletes[j].silver;
    temp_c = athletes[j].gold;
    temp_d = athletes[j].total;
    result_found++;//variable to tell if there is a result

   }

}
if(result_found != 0){//using variable to print out result
printf("Bronze\tSilver\tGold\ttotal\n\n%d\t%d\t%d\t%d\n",temp_a,temp_b,temp_c,temp_d);
}
if(result_found == 0){
    printf("No results found\n");
}

}
/*****************************************************************************************************************/
void compareSport(char* sport, int i){
int j,k,z;
j = 0; k = 0;z=0;
int temp_a = 0;
char temp_b[150] = {""};
int temp_total[1000] = {0};
char temp_name[1000][150] = {""};

for(j = 0; j<i; j++){

    if(strcasecmp(athletes[j].sport,sport) == 0){
        temp_total[k] = athletes[j].total;
        strncpy(temp_name[k],athletes[j].name,150);// taking in totals and names
        k++;
    }
}
for(j = 0; j<(k-1);++j){

for(z = 0; z< (k-j-1); ++z){
            if(temp_total[z]<temp_total[z+1]){

            temp_a = temp_total[z];
            temp_total[z] = temp_total[z+1];
            temp_total[z+1] = temp_a;

            strcpy(temp_b,temp_name[z]);//swap names as well as total
            strcpy(temp_name[z], temp_name[z+1]);
            strcpy(temp_name[z+1],temp_b);



        }
    }
}
for(j = 0; j<k;j++){
    printf("%s\t\t\t\t\t%d\n",temp_name[j],temp_total[j]);
}




}
/**************************************************************************************************************/
void compareCountry(char *country,int i){

int j;
j = 0;
int temp_a,num_results;
temp_a = 0;//holds country total medals
for(j = 0; j<i; j++){

    if(strcasecmp(athletes[j].country,country) == 0){
        temp_a += athletes[j].total;//totaling up all medals from athletes of country entered
        num_results++;//variable to check if there are any results
    }
}
if(num_results == 0){
    printf("no results found\n");

}
if(num_results != 0){
printf("%s:\t%d\n",country,temp_a);
}
}
/****************************************************************************************************************/
void results_sport_year(char *sport, int year, int i){//gets the amount of medals won that year in a particular sport
int j,num_results;// was not particularly sure what results were wanted
num_results = 0;
int temp_a,temp_b,temp_c;
temp_a =0;temp_b = 0;temp_c = 0;
for(j = 0; j<i; j++){

    if(strcasecmp(athletes[j].sport,sport) == 0 && (athletes[j].year == year)){
       temp_a += athletes[j].bronze;
       temp_b += athletes[j].silver;
       temp_c += athletes[j].gold;
       num_results++;
    }
}
if(num_results != 0){
printf("year: %d\n",year);
printf("Bronze\tSilver\tGold\t\n%d\t%d\t%d\n",temp_a,temp_b,temp_c);
}
if(num_results == 0){
    printf("No results found\n");
}

}
