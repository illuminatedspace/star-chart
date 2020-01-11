# Technical Design

## Questions

- Prioritizing/Ordering Tasks

## Assumptions

- All _timestamp_ types are ISO Timestamps unless otherwise noted
- A user with 50 unique stars created every day for 1 year (365 days) for 10 years will have 182,500 stars, which is well within tolerance for UUIDv4

## Star

Each item the user creates is called a Star
All Stars have at the very least a timestamp

_Properties_

- id _UUID_
- createdAt _timestamp_
- type _Enum of Star Categories_
- ?constellations _array of strings?_ (tag)

### Star Categories

#### Events

_Properties_

- startTime _timestamp_
- endTime _timestamp_
- name _string_
- type: event

#### Notes

- body
- type: note
- ?title

#### Tasks/Goals

All tasks are child tasks. "Top level" tasks in the UI are still child tasks to aid with ordering

- name
- type: task
- status: [notStarted] _enum of statuses notStarted, complete_
- goal _boolean_
- ?parentTask: _id of another task_ (maybe not needed)
- ?childrenTasks: _id of another task_
- ?body _string_
- ?dueDate _timestamp_
- ?completedAt _timestamp_

#### Moods

- rating _number 1-5_
- ?emotion _enum of emotions: anger, anxious, sad, happy_

#### Symptoms/Side Effects

- name _user defined enum or string_
- startTime: [now] _timestamp_
- ?endTime _timestamp_
- ?severity _number 1-10_
- ?body

#### Medications

- name _user defined enum or string_
- dose _string_ number + unit(pills, mg, droppers, cups)
- frequency _frequency enum_
- frequencyStartAt _timestamp_
- visual appearance _string, or enum of little images + colors_
- pills left _number_

## Views

### Agenda

calendar view by certain time span with toggleable tasks, events, reminders for that time span

### Goal

All items related to a goal over time

### Constellation

View all items related to a constellation(tag)

## Reminders

One time
By frequency
By condition (medication pills left reminder)

## Data Visualization

Interactions between stars over time

## Visual Elements

Notes customization with visual elements, gifs, and stickers
Themes for visual appearance

## Client Types

- web
- mobile (react native)
- text (limited)
- ?desktop (electron)
- api

## License

https://fair.io/#faq

## UI

### Notes

- support some kind markdown on backend, WYSIWYG on front end
  https://github.com/jpuri/react-draft-wysiwyg
  https://github.com/ianstormtaylor/slate

## Exports/Imports

- export all data types
- import google calendar data types

## Prioritization

_Parent task has order array as attribute_

- When reordering happens, only need to edit one attribute on one item

Research
https://github.com/clauderic/react-sortable-hoc

## Backend Architecture

### Database

- DynamoDb

### Routing

- API Gateway

### Functions

- Lambda

### Non Database Storage

- S3

### CDN

- Cloudfront
