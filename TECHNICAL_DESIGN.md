# Technical Design

## Questions

- Should Body types support markdown syntax

## Assumptions

All _timestamp_ types are ISO Timestamps unless otherwise noted

## Star

Each item the user creates is called a Star
All Stars have at the very least a timestamp

_Properties_

- createdAt _timestamp_
- type _Enum of Star Categories_
- ?tags _array of strings?_ (Possibly call Constellations)

### Star Categories

#### Events

_Properties_

- endTime _timestamp_
- name _string_
- type: event

#### Journal Entries

- body
- ?title

#### Tasks

- name
- ?body _string_
- ?dueDate _timestamp_
- complete _enum of statuses_
-

#### Goals

#### Moods

#### Symptoms

#### Medications
