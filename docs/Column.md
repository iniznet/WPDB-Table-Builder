# Column

> **Related Pages**
>
> » [Schema](Schema.md)

The model of a tables column.

# SETTERS

***

## type( string $type ): Column

> @param string $type Defines the column type, only valid MYSQL types should be used  
> @return Column  

 

```php
$schema = new Schema('table', function(Schema $schema): void{
    // Defined a column with the type of TEXT
    $schema->column('foo')->type('text');
]);
```

```sql
CREATE TABLE table(
    foo TEXT,
);
```

***

## length( int $length ): Column

> @param int $length Defines the column length, only valid MYSQL lengths should be used  
> @return Column  

 

```php
$schema = new Schema('table', function(Schema $schema): void{
    // Defined a column with the type of LENGTH
    $schema->column('foo')->type('int')->length(12);
]);
```

```sql
CREATE TABLE table(
    foo INT(11)  NOT NULL,
);
```

***

## precision( int $precision ): Column

> @param int $precision Defines the precision of floating point columns. 
> @return Column  

 

```php
$schema = new Schema('table', function(Schema $schema): void{
    // Defined a column with the type of LENGTH
    $schema->column('foo')->type('decimal')->length(12)->precision(2);
]);
```

```sql
CREATE TABLE table(
    foo DECIMAL(12, 2)  NOT NULL,
);
```

***

## nullable( string $nullable = true ): Column

> @param string $nullable Defines if the column can allow NULL as a value  
> @return Column  

 

```php
$schema = new Schema('table', function(Schema $schema): void{
    // Defined a column with the type of nullable
    $schema->column('foo')->varchar(255)->nullable(true);
    $schema->column('bar')->text()->nullable(false);
]);
```

```sql
CREATE TABLE table(
    foo VARCHAR(255) NULL, 
    bar TEXT NOT NULL, 
);
```

***

## default( string $default ): Column

> @param string $default Defines the default value for a column
> @return Column  

 

```php
$schema = new Schema('table', function(Schema $schema): void{
    // Defined a column with the type of nullable
    $schema->column('foo')->varchar(255)->default('HAPPY');
]);
```

```sql
CREATE TABLE table(
    foo VARCHAR(255) NOT NULL DEFAULT 'HAPPY'
);
```

***

## auto_increment( bool $auto_increment = true ): Column

> @param bool $auto_increment Denotes if the column should auto increment.  
> @return Column  

 

```php
$schema = new Schema('table', function(Schema $schema): void{
    // Defined a should be set to auto increment
    $schema->column('foo')->int(11)->auto_increment(true);
]);
```

```sql
CREATE TABLE table(
    foo INT(11) NOT NULL AUTO_INCREMENT
);
```

> As per MYSQL standards, only a single column (which is a key) can be set to  auto_increment  
>  

***

## unsigned( bool $unsigned = true ): Column

> @param bool $auto_increment Denotes if the column should be an unsigned numerical value.    
> @return Column  

 

```php
$schema = new Schema('table', function(Schema $schema): void{
    // Defined a should be set to be unsigned
    $schema->column('foo')->int()->unsigned(true);
]);
```

```sql
CREATE TABLE table(
    foo INT UNSIGNED 
);
```

> Can only be used on numerical column types.

***

# Type Helpers (Shortcuts)

## json(): Column

> @return Column  

Defines a column as JSON

> **IF USING MYSQL A DEFAULT CAN NOT BE DEFINED, YOU CAN USING MARIADB**

```php
$schema = new Schema('table', function(Schema $schema): void{
    // Using helper
    $schema->column('json_data')->json();
    // Verbose
    $schema->column('json_data')->type('json');
});
```

***

## varchar( ?int $length = null ): Column

> @param int|null $length Sets the max length of the columns value, passing null omits setting length.  
> @return Schema  

Defines a `VARCHAR(length)` with an optional length

```php
$schema = new Schema('table', function(Schema $schema): void{
    // Using helper
    $schema->column('some_string')->varchar(16);
    // Verbose
    $schema->column('some_string')->type('varchar')->length(16);
});
```

***

## text( ?int $length = null ): Column

> @param int|null $length Sets the max length of the columns value, passing null omits setting length.  
> @return Column  

Defines a `TEXT(length)` with an optional length

```php
$schema = new Schema('table', function(Schema $schema): void{   
    // Using helper
    $schema->column('some_string')->text(16);
    // Verbose
    $schema->column('some_string')->type('text')->length(16);
});
```

***

## int( ?int $length = null ): Column

> @param int|null $length Sets the max length of the columns value, passing null omits setting length.  
> @return Column  

Defines a `INT(length)` with an optional length

```php
$schema = new Schema('table', function(Schema $schema): void{
    // Using helper
    $schema->column('some_string')->int(16);
    // Verbose
    $schema->column('some_string')->type('int')->length(16);
});
```

***

## float( ?int $length = null, ?int $precision = null ): Column

> @param int|null $length Sets the max length of the columns value, passing null omits setting length.  
> > @param int|null $precision Sets number of decimal places to allow.    
> @return Column  

Defines a `FLOAT(length, precision)` with an optional length

```php
$schema = new Schema('table', function(Schema $schema): void{
    // Using helper
    $schema->column('some_string')->float(16,4);
    // Verbose
    $schema->column('some_string')->type('float')->length(16)->precision(4);
});
```

***

## double( ?int $length = null, ?int $precision = null  ): Column

> @param int|null $length Sets the max length of the columns value, passing null omits setting length.  
> > @param int|null $precision Sets number of decimal places to allow.    
> @return Column  

Defines a `DOUBLE(length, precision)` with an optional length

```php
$schema = new Schema('table', function(Schema $schema): void{
    // Using helper
    $schema->column('some_string')->double(16,2);
    // Verbose
    $schema->column('some_string')->type('double')->length(16)->precision(2);
});
```

***

## unsigned_int( ?int $length = null ): Column

> @param int|null $length Sets the max length of the columns value, passing null omits setting length.  
> @return Column  

Defines a `UNSIGNED INT(length)` with an optional length

```php
$schema = new Schema('table', function(Schema $schema): void{
    // Using helper
    $schema->column('some_string')->unsigned_int(16);
    // Verbose
    $schema->column('some_string')->type('unsigned_int')->length(16);
});
```

***

## unsigned_medium( ?int $length = null ): Column

> @param int|null $length Sets the max length of the columns value, passing null omits setting length.  
> @return Column  

Defines a `UNSIGNED INT(length)` with an optional length

```php
$schema = new Schema('table', function(Schema $schema): void{
    // Using helper
    $schema->column('some_string')->unsigned_medium(16);
    // Verbose
    $schema->column('some_string')->type('unsigned_medium')->length(16);
});
```

***

## unsigned_big( ?int $length = null ): Column

> @param int|null $length Sets the max length of the columns value, passing null omits setting length.  
> @return Column  

Defines a `UNSIGNED INT(length)` with an optional length

```php
$schema = new Schema('table', function(Schema $schema): void{
    // Using helper
    $schema->column('some_string')->unsigned_big(16);
    // Verbose
    $schema->column('some_string')->type('unsigned_big')->length(16);
});
```

***

## date( ?string $default = null ): Column

> @param string|null $default  
> @return Column  

Defines a `DATE` with an optional default value

```php
$schema = new Schema('table', function(Schema $schema): void{
    // Using helper
    $schema->column('some_string')->date('2012-12-31');
    // Verbose
    $schema->column('some_string')->type('date')->default('2012-12-31');
});
```

***

## datetime( ?string $default = null ): Column

> @param string|null $default  
> @return Column  

Defines a `DATETIME` with an optional default value

```php
$schema = new Schema('table', function(Schema $schema): void{
    // Using helper
    $schema->column('some_string')->datetime('2012-12-31 23:59:59');
    // Verbose
    $schema->column('some_string')->type('datetime')->default('2012-12-31 23:59:59');
});
```

# Getters

## get_name(): string

> @return string  

Returns the defined column name.

*** 

## get_name(): string

> @return string  

Returns the defined column name.

*** 

## get_type(): string|null

> @return string|null  

Returns the type if defined (null if not)

*** 

## get_length(): int|null

> @return int|null  

Returns the length if defined (null if not)

*** 

## get_precision(): int|null

> @return int|null  

Returns the precision if defined (null if not)

*** 

## is_nullable(): bool

> @return bool  

Returns the column is nullable (assumes false if not defined.)

*** 

## get_default(): mixed

> @return mixed  

Returns the default value, if not set will return null.

*** 

## is_auto_increment(): bool

> @return bool  

Returns the column is set to auto increment (assumes false if not defined.)

*** 

## is_unsigned(): bool

> @return bool  

Returns the column is set to unsigned (assumes false if not defined.)

*** 

## export(): stdClass

> @return object{  
> name : string,  
> type : string,  
> length : int|null,  
> precision : int|null,  
> nullable : bool,  
> default : string|int|float,  
> unsigned : bool,  
> auto_increment : bool,  
> }

Returns a stdClass object with the columns values.
