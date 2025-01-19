# Tournament SQL Database Project (Cricket Focused)

This project is a SQL database designed to manage data for a cricket tournament. It includes tables for teams, players (with specializations for batsmen and bowlers), coaches, umpires, match schedules, match summaries, match information, and point tables.

## Database Schema

The database schema includes the following tables:

*   **player:** Stores general player information.
    *   `player_id` (varchar(20)): Primary Key
    *   `tm_id` (varchar(20)): Foreign Key referencing `team`
    *   `player_name` (varchar(50))
    *   `date_of_birth` (date)
    *   `player_category` (enum('Bowler', 'Batsman', 'Allrounder'))
    *   `batting_or_bowling_style` (enum('Right Handed', 'Left Handed', '360 Degree'))
    *   `country_name` (varchar(50))

*   **batsman:** Stores specific batsman statistics.
    *   `player_id` (varchar(20)): Primary Key, Foreign Key referencing `player`
    *   `tm_id` (varchar(20)): Foreign Key referencing `team`
    *   `batting_style` (enum('Left Handed Batsman', 'Right Handed Batsman', '360 Degree Batsman'))
    *   `total_runs` (int(5))
    *   `average` (float)
    *   `top_score` (int(5))
    *   `total_match_played` (int(3))
    *   `strike_rate` (float)
    *   `100s` (smallint(4))
    *   `50s` (smallint(3))
    *   `jersey_number` (smallint(3))

*   **bowler:** Stores specific bowler statistics.
    *   `player_id` (varchar(20)): Primary Key, Foreign Key referencing `player`
    *   `tm_id` (varchar(20)): Foreign Key referencing `team`
    *   `bowling_style` (enum('Left Handed', 'Right Handed'))
    *   `average_speed` (varchar(10))
    *   `higest_speed` (varchar(10))
    *   `economy_rate` (float)
    *   `bowling_average` (float)
    *   `best_bowling_figure` (varchar(20))
    *   `batting_average` (float)
    * `jersey_number` (int(3))

*   **team:** Stores team information.
    *   `tm_id` (varchar(20)): Primary Key
    *   `tm_name` (varchar(50))
    *   `head_coach_id` (varchar(20)): Foreign Key referencing `coach`
    *   `head_coach_name` (varchar(100))
    *   `captain_id` (varchar(20)): Foreign Key referencing `player`
    *   `Console Intry name` (varchar(50)): *This seems like a typo; consider renaming to something more descriptive like `team_abbreviation` or similar.*

*   **coach:** Stores coach information.
    *   `coach_id` (varchar(20)): Primary Key
    *   `coach_name` (varchar(50))
    *   `country` (varchar(100))
    *   `present_coach_of` (varchar(100))

*   **schedule:** Stores match schedule information.
    *   `schedule_id` (varchar(20)): Primary Key
    *   `match_id` (varchar(20))
    *   `venue` (varchar(20))
    *   `country` (varchar(20))
    *   `Stadium` (varchar(100))
    *   `Time` (date) *It's recommended to use `DATETIME` or `TIMESTAMP` for more precision.*

*   **umpire:** Stores umpire information.
    *   `umpire_name` (varchar(50))
    *   `umpire_id` (varchar(20)): Primary Key
    *   `total_umpired_matches` (int(3))
    *   `country` (varchar(50))
    *   `controversy` (text)

*   **match_summary:** Stores match summary information.
    *   `match_id` (varchar(20)): Primary Key
    *   `man_of_the_match` (varchar(20)): Foreign Key referencing `player`
    *   `top_run_scorer` (varchar(20)): Foreign Key referencing `player`
    *   `best_bowler` (int(20)): *This should likely be a foreign key referencing `player`.*

*   **match_info:** Stores detailed match information.
    *   `match_id` (varchar(20)): Primary Key
    *   `umpire1_name` (varchar(50))
    * `umpire1_id` (varchar(20)): Foreign Key referencing `umpire`
    *   `umpire2_name` (varchar(50))
    * `umpire2_id` (varchar(20)): Foreign Key referencing `umpire`
    *   `umpire3_name` (varchar(50))
    * `umpire3_id` (varchar(20)): Foreign Key referencing `umpire`
    *   `team1_name` (varchar(50))
    *   `tm1_id` (varchar(20)): Foreign Key referencing `team`
    *   `team2_name` (varchar(50))
    *   `tm2_id` (varchar(20)): Foreign Key referencing `team`
    *   `over` (smallint(2))

*   **point_table:** Stores team points information.
    *   `tm_id` (varchar(20)): Foreign Key referencing `team`
    *   `point` (smallint(2))

## Database Project Functions

This database enables the following functions:

*   **Managing Teams and Players:** Add, update, and delete teams and players, including specific statistics for batsmen and bowlers.
*   **Scheduling Matches:** Create and manage match schedules, including venue, date, and time.
*   **Recording Match Results:** Store match summaries, including man of the match and top performers.
*   **Tracking Tournament Progress:** Generate point tables and other statistics to track tournament progress.
*   **Generating Reports:** Create reports on team standings, player statistics, and other tournament data.

## Technologies Used

*   SQL (Likely MySQL, PostgreSQL, or other relational database management system)

## Further Development

*   **Data Validation:** Implement comprehensive data validation rules (e.g., check for valid dates, data types, and referential integrity).
*   **Stored Procedures and Triggers:** Use stored procedures to encapsulate complex operations and triggers to enforce data integrity.
*   **User Interface:** Develop a user interface (web or desktop application) to interact with the database.
*   **Reporting Enhancements:** Implement more advanced reporting features and data visualization.
*   **Tournament Logic:** Implement logic for handling different tournament formats (round-robin, knockout, etc.).

