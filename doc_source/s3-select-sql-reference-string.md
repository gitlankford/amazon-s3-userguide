# String functions<a name="s3-select-sql-reference-string"></a>

Amazon S3 Select supports the following string functions\.

**Topics**
+ [CHAR\_LENGTH, CHARACTER\_LENGTH](#s3-select-sql-reference-char-length)
+ [LOWER](#s3-select-sql-reference-lower)
+ [SUBSTRING](#s3-select-sql-reference-substring)
+ [TRIM](#s3-select-sql-reference-trim)
+ [UPPER](#s3-select-sql-reference-upper)

## CHAR\_LENGTH, CHARACTER\_LENGTH<a name="s3-select-sql-reference-char-length"></a>

`CHAR_LENGTH` \(or `CHARACTER_LENGTH`\) counts the number of characters in the specified string\.

**Note**  
`CHAR_LENGTH` and `CHARACTER_LENGTH` are synonyms\.

### Syntax<a name="s3-select-sql-reference-char-length-syntax"></a>

```
CHAR_LENGTH ( string )
```

### Parameters<a name="s3-select-sql-reference-char-length-parameters"></a>

 *`string`*   
The target string that the function operates on\.

### Examples<a name="s3-select-sql-reference-char-length-examples"></a>

```
CHAR_LENGTH('')          -- 0
CHAR_LENGTH('abcdefg')   -- 7
```

## LOWER<a name="s3-select-sql-reference-lower"></a>

Given a string, `LOWER` converts all uppercase characters to lowercase characters\. Any non\-uppercased characters remain unchanged\.

### Syntax<a name="s3-select-sql-reference-lower-syntax"></a>

```
LOWER ( string )
```

### Parameters<a name="s3-select-sql-reference-lower-parameters"></a>

 **`string`**   
The target string that the function operates on\.

### Examples<a name="s3-select-sql-reference-lower-examples"></a>

```
LOWER('AbCdEfG!@#$') -- 'abcdefg!@#$'
```

## SUBSTRING<a name="s3-select-sql-reference-substring"></a>

Given a string, a start index, and optionally a length, `SUBSTRING` returns the substring from the start index up to the end of the string, or up to the length provided\.

**Note**  
The first character of the input string has an index position of 1\.  
 If `start` is < 1, with no length specified, then the index position is set to 1\. 
 If `start` is < 1, with a length specified, then the index position is set to `start + length -1`\. 
 If `start + length -1` < 0, then an empty string is returned\. 
 If `start + length -1` > = 0, then the substring starting at index position 1 with the length `start + length - 1` is returned\. 

### Syntax<a name="s3-select-sql-reference-substring-syntax"></a>

```
SUBSTRING( string FROM start [ FOR length ] )
```

### Parameters<a name="s3-select-sql-reference-substring-parameters"></a>

 **`string`**   
The target string that the function operates on\.

 **`start`**   
The start position of the string\.

 **`length`**   
The length of the substring to return\. If not present, proceed to the end of the string\.

### Examples<a name="s3-select-sql-reference-substring-examples"></a>

```
SUBSTRING("123456789", 0)      -- "123456789"
SUBSTRING("123456789", 1)      -- "123456789"
SUBSTRING("123456789", 2)      -- "23456789"
SUBSTRING("123456789", -4)     -- "123456789"
SUBSTRING("123456789", 0, 999) -- "123456789" 
SUBSTRING("123456789", 1, 5)   -- "12345"
```

## TRIM<a name="s3-select-sql-reference-trim"></a>

Trims leading or trailing characters from a string\. The default character to remove is a space \(`' '`\)\.

### Syntax<a name="s3-select-sql-reference-trim-syntax"></a>

```
TRIM ( [[LEADING | TRAILING | BOTH remove_chars] FROM] string )
```

### Parameters<a name="s3-select-sql-reference-trim-parameters"></a>

 **`string`**   
The target string that the function operates on\.

 `LEADING` \| `TRAILING` \| `BOTH`   
This parameter indicates whether to trim leading or trailing characters, or both leading and trailing characters\.

 **`remove_chars`**   
The set of characters to remove\. `remove_chars` can be a string with a length > 1\. This function returns the string with any character from `remove_chars` found at the beginning or end of the string that was removed\.

### Examples<a name="s3-select-sql-reference-trim-examples"></a>

```
TRIM('       foobar         ')               -- 'foobar'
TRIM('      \tfoobar\t         ')            -- '\tfoobar\t'
TRIM(LEADING FROM '       foobar         ')  -- 'foobar         '
TRIM(TRAILING FROM '       foobar         ') -- '       foobar'
TRIM(BOTH FROM '       foobar         ')     -- 'foobar'
TRIM(BOTH '12' FROM '1112211foobar22211122') -- 'foobar'
```

## UPPER<a name="s3-select-sql-reference-upper"></a>

Given a string, `UPPER` converts all lowercase characters to uppercase characters\. Any non\-lowercased characters remain unchanged\.

### Syntax<a name="s3-select-sql-reference-upper-syntax"></a>

```
UPPER ( string )
```

### Parameters<a name="s3-select-sql-reference-upper-parameters"></a>

 **`string`**   
The target string that the function operates on\.

### Examples<a name="s3-select-sql-reference-upper-examples"></a>

```
UPPER('AbCdEfG!@#$') -- 'ABCDEFG!@#$'
```