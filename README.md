# PDF Calendar Generator for PHP

[![Latest Stable Version](https://poser.pugx.org/efectn/php-pdf-calendar/v/stable)](https://packagist.org/packages/efectn/php-pdf-calendar) [![Latest Unstable Version](https://poser.pugx.org/efectn/php-pdf-calendar/v/unstable)](https://packagist.org/packages/efectn/php-pdf-calendar) [![Total Downloads](https://poser.pugx.org/efectn/php-pdf-calendar/downloads)](https://packagist.org/packages/efectn/php-pdf-calendar) [![Monthly Downloads](https://poser.pugx.org/efectn/php-pdf-calendar/d/monthly)](https://packagist.org/packages/efectn/php-pdf-calendar)


**Generate PDF month calendars with autoscaling/sizing.**

Originally forked from [a-schild/pdfcalendarbuilder](https://github.com/a-schild/pdfcalendarbuilder), but under active maintenance. 

With the addMonth() introduced in 1.0.8 you can generate a PDF containing
multiple months. Each month will be on it's own page then.

## Unique Features
- The class can try to put everything on one page.
- In an normal calendar, all rows have the same height.
- This library can shrink/expand rows, so everything fits on one page.
See setResizeRowHeightsIfNeeded(true/false);

- If this is not enough, it can reduce the font size until everything fits on one page.
See setShrinkFontSizeIfNeeded(true/false);

## Installation & Usage:
Run: `composer require efectn/php-pdf-calendar`

### Creating the class and generate calendar
```
$cal = new efectn\PDFCalendarBuilder\CalendarBuilder(1, 2019, "Calendar title", true, 'mm', 'A4');
$cal->startPDF();
$cal->addEntry($startDate, $endDate, "Entry 1", "#000000", "#fffff");
$cal->buildCalendar();
$cal->Output("calendar.pdf", "I");
```

### Creating the class and generate calendar for 3 months (Required version 1.0.7 or higher)
```
$cal = new efectn\PDFCalendarBuilder\CalendarBuilder(1, 2019, "Calendar title Jan", true, 'mm', 'A4');
$cal->startPDF();
$cal->addEntry($startDate1, $endDate1, "Entry 1", "#000000", "#ffffff");
$cal->buildCalendar();
$cal->addMonth(2, 2019, "Title for Feb");
$cal->addEntry($startDate2, $endDate2, "Entry 1", "#000000", "#ffffff");
$cal->buildCalendar();
$cal->addMonth(3, 2019, "Title for March");
$cal->addEntry($startDate3, $endDate3, "Entry 1", "#000000", "#ffffff");
$cal->buildCalendar();
$cal->Output("calendar.pdf", "I");
```

## Examples
- Empty calendar, no entries, just a month grid
  ![Empty calendar ](doc/img/calendar-empty.png)
- Overflowing boxes in normal libraries
  ![Box overflow in normal calendars](doc/img/calendar-overflow.png)
- Resize row heights to adapt space usage
  ![Resize rows height](doc/img/calendar-resize-row2.png)
- Resize row heights and shrink font size if needed
  ![Resize rows and shrink font](doc/img/calendar-resize-rows-shrink-fontsize.png)
- Day spanning events
  ![Events which span days](doc/img/calendar-day-spanning.png)

(C) 2019-2022 A.Schild, (C) 2022 Efe Çetin

