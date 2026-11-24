# Constitution
Version 1.0, YYYY-MM-DD

## Purpose and scope
- The product does: ...
- The product does not: ...

## Architecture invariants
- Single source of truth for <entity>: <module or table>
- Data flows in one direction: <A> -> <B> -> <C>
- Module boundaries: <module> never imports from <module>

## Stack lock
- Language, framework, database, hosting: ...
- New runtime dependency requires a decision record

## Quality bar
- Mutation score on changed code: at least <n>%
- No silent fallbacks; errors are visible
- No mock data outside tests

## Data and security
- Personal data: where it may live, where it never goes
- Row-level security on every user-data table

## Agent behaviour
- Ask before: schema changes, deleting files, renaming glossary terms
- Never: write to production, edit applied migrations, disable tests

## Amendments
| Version | Date | Change | Reason |
| --- | --- | --- | --- |
| 1.0 | YYYY-MM-DD | Initial version | |
