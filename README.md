# Linux-Project on Library Managemnent System using Script Shell
# addBook(): Function to add a new book to the library. 
 
add_book() { 
echo "Enter book title:" 
read title 
echo "Enter book author:" 
read author 
echo "Enter number of copies:" 
read copies 
 
# checking whether inputs are empty or not 
if [ -z "$title" ] || [ -z "$author" ] || [ -z "$copies" ]; then 
echo "All fields are mandatory." 
 
elif ! [[ "$copies" =~ ^[0-9]+$ ]]; then 
echo "Number of copies must be a valid number." 
else 
 
# deleteBook(): Function to remove a book from the library. 
 
delete_book() { 
echo "Enter book ID to delete:" 
read book_id 
 
# Check if the input is a valid number 
if ! [[ "$book_id" =~ ^[0-9]+$ ]]; then 
echo "Invalid book ID. Please enter a valid number." 
else 
# Execute delete command in SQLite 
sqlite3 $DB_NAME "DELETE FROM books WHERE id = 
$book_id;" 
 
# Check if the deletion was successful by checking the return code 
if [ $? -eq 0 ]; then 
echo "Book deleted successfully." 
else 
14  

# listBooks(): Function to list all books in the library. 
 
 
# Function to view all books 
view_books() { 
sqlite3 $DB_NAME "SELECT id, title, author, copies, issued FROM 
books;" 
} 
