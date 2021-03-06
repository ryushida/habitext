# habitext

Habitext is a habit tracking tool that generates PDF reports from habit data in markdown files.

[Example PDF](https://github.com/ryushida/habitext/blob/master/example_habits/reports/20200715_habits.pdf)

# Habit Format

Habits are in the following format in a directory.

```
habit folder
∟ 01_habit1.md
∟ 02_habit2.md
```

The file name can by anything, but the order of the habits in the PDF is determined by the order of the files in the folder.

#### **`01_habit1.md`**
```md
# Metadata

Name: Habit1
Goal: Goal for habit1

# Log

- MMMM-DD-YY
  - Note1
    - HH:MM
- MMMM-DD-YY
  - Note2
    - HH:MM
  - Note3
    - HH:MM
  - Note4
    - HH:MM
```

# Usage

## Local
1. Install python 3 and pip
2. Install required packages
```bash
pip install pandas plotnine reportlab
```
3. Clone Repository
```bash
git clone https://github.com/ryushida/habitext.git
```
4. Update configuration in config.ini
5. Run script
```bash
cd habitext
python habitext.py
```

## Docker

1. Install Docker
2. Clone and update settings
```bash
git clone https://github.com/ryushida/habitext.git
```
2. Update configuration in config.ini
3. Build Docker Container
```bash
cd habitext
docker build -t habitext .
```
3. Run script in Docker Container

```bash
# Replace C:\Directory\of\habits with local directory where you store the .md files
docker run -it -v C:\Directory\of\habits:/habits/ habitext
```

You may need to set the timezone for the container. One way is by replacing the 'TZ database name' in the following command. Get your timezone from the 'TZ database name' column in the [list of tz database time zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).
```bash
docker run --rm -it -v C:\Files\Repos\habits:/habits/ -e "TZ='TZ database name'" habitext
```