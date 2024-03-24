#include <stdio.h>

struct Date {
    int day;
    int month;
    int year;
};


struct Date addOneDay(struct Date d) {
    int daysInMonth[] = {31,28,31,30,31,30,31,31,30,31,30,31};

    d.day++;

    if ((d.year % 4 == 0 && d.year % 100 != 0) || (d.year % 400 == 0)) {
        daysInMonth[1] = 29; 
    }

    if (d.day > daysInMonth[d.month - 1]) {
        d.day = 1; 
        d.month++;

        if (d.month > 12) {
            d.month = 1; 
            d.year++; 
        }
    }

    return d;
}

int main() {
    struct Date today;

    printf("Masukkan tanggal hari ini (format: hari bulan tahun): ");
    scanf("%d %d %d", &today.day, &today.month, &today.year);

    struct Date tomorrow = addOneDay(today);

    printf("Besok adalah tanggal: %d-%d-%d\n", tomorrow.day, tomorrow.month, tomorrow.year);

    return 0;
}

      
