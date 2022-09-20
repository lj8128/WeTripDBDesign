# WeTrip Database Schema

## How to Use
1. Clone the repository.
2. Copy and paste the code in `WeTripSchema.txt` to dbdiagram's interface.
3. Modify the code through dbdiagram's interface.
4. Replace the code in `WeTripSchema.txt` with your new code.
5. Push your changes.

## Comments on dbdiagram's Syntax
Reference <a href="https://dbdiagram.io/d">dbdiagram's example schema</a> to see how its syntax works. It's pretty self-explanatory, except:

1. Note that dbdiagram makes us name our tables in the format `<schema>.<table_name>`. If we don't specify a schema, dbdiagram puts in 'public' as the schema name for the default. This is why I've temporarily named all the tables `WT.<table_name>`, where 'WT' stands for WeTrip.

2. Say that you want to declare that the attribute id of the user table: (i) is a primary key, and (ii) has a one-to-many relationship with the user-trip table's trip_id attribute. Then you would write:
```
  Table user {
    id int[pk, ref: < user-trip.trip_id]
  }
```

If you want to add a comment that the user's id should be an SSN, you would code:
```
  Table user {
    id int[pk, ref: < user-trip.trip_id, node: 'user's SSN']
  }
```

Note that the comment is enclosed in single quotes.

3. dbdiagram does not let us specify, for example, a many-to-one relationship from `WT.budget.(category, amount)` to `WT.trip.id`. This is why I've resorted to specifying a many-to-one relationship from `WT.budget.trip_id` to `WT.trip.id`. Maybe there's a better way to do this, in which case, someone can suggest it and modify this paragraph.