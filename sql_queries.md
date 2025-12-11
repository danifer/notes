
SQL and PostgreSQL query examples for regex operations, string comparison, and address matching with special character handling.

# Compare address partials on two fields, accounting for inconsistencies with spacing and special characters.
    CREATE TEMP VIEW _results AS (
        SELECT
            starts_with(
                regexp_replace(
                    address_line1, '\W+', '', 'g'
                ),
                regexp_replace(
                    split_part(address_formatted, ',', 1) , '\W+', '', 'g'
                )
            ) AS has_match,
            location_id,
            location_number
        FROM location
        WHERE account = 'XXX'
    );


    SELECT location_number FROM _results WHERE has_match = false;

