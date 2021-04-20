# Capstone: Restaurant Reservation System Backend

Starter Restaurant Reservation is an online system used to maintain record for customer reservations. A reservation will be create for customers which include details of Number of person, Phone Number, Reservation Time, The reservation will not be create before 10:00 am and after 9:30 pm and for the past days. This system will also keep track which reservation is booked, seated and finished. The manager can also search reservation by entering the Phone Number or date.

## Live Application Link
https://starter-restaurant-reservation-backend.vercel.app/

The table below listing the existing routes in the `./back-end` folder:

  ## Routes
  ### `GET /reservations`
  ### `POST /reservations`
  ### `GET /reservations/:reservation_Id`
  ### `PUT /reservations/:reservation_Id/status`
  ### `GET /tables`
  ### `POST /tables`
  ### `PUT /tables/:table_id/seat`
  ### `DELETE /tables/:table_id/seat`

## GET /reservations
This path will give a record of all reservations created for customers

## POST /reservations
This path will take all parameters(first_name, last_name, phone_number, reservation_date, reservation_time, people) require for creating a reservation. The reservation will create if data is valid but if any of the parameter is missing the system will not create reservation for customer and throw validation errors.

## GET /reservations/:reservation_Id
This path will take `reservation_id` as parameter and will search for reservation by Id. If Id exist than it will return the record found for the Id else it will raise validation error Id not found.

## PUT reservations/:reservation_Id/status
This path will take `reservation_id` and `status` as parameter. If Id exist than it will update the status by the value provided for status in parameters. The status can only be updated from `booked` to `seated` and from `seated` to `finished`. The status cannot be updated from `finished` to `seated/booked` and from `booked` to `finished`. If reservation id is not found or status will be other than `booked/seated/finished` or status update request will be from `finished` to `seated/booked` or from `booked` to `finished` then the reservation will not be update and system will throw validations error.

## GET /tables
This path will give a record of all tables created for reservations

## POST /tables
This path will take all parameters(table_name, capacity, ) require for creating a table. The table will create if data is valid but if any of the parameter is missing the system will not create table and throw validation errors.


## PUT /tables/:table_id/seat
This path will take `reservation_id` and `table_id` as parameter. The table `reservation_id` will update by the Id present in parameters if both `reservation_id` and `table_id` is valid, table is not occupied and table capacity is sufficient. If any of these validations fail the table will not be update and it will throw validations error

## DELETE /tables/:table_id/seat
This path will take `table_id` as parameter and updates table's `reservation_id` by `null` if `table_id` is valid and `reservation_id` is not `null` else the system will throw validation errors
