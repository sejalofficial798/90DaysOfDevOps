**YAML Basics**

you can write YAML or YML  both are same
with command cat person.yaml I got output-
$ cat person.yml
name: Sejal Jadhav
role: AWS Devops Engineer
experience_years: 4 years
learning: "true"

`task 02`
There are 2 types to list in yml 
1. is with block style 
eg :
tools:
  - Terraform
  - Jenkins
2. Inline style 
eg: 
hobbies: [Drawing, Paintiing]

`Task 03`
If we give tab for indentation instead of 2 spaces it will not consider dont take it as nested structure.
YAML only allows spaces
 Even 1 tab = invalid YAML

Because YAML structure depends strictly on spaces.

|  = Keep formatting
>  = Join lines

`Task 04`
Literal blocks- preservs new lines. we can use-To writing shell scripts, Config files, Anything where line breaks matter

Folded block-
Converts newlines into spaces. We can use it for Long descriptions, Paragraph text, When line breaks are not important

`Task 05`
Errors observed
person.yml
  5:17      error    trailing spaces  (trailing-spaces)
  6:3       warning  missing starting space in comment  (comments)
  6:2       warning  comment not indented like content  (comments-indentation)
  6:45      error    trailing spaces  (trailing-spaces)
  8:1       error    wrong indentation: expected at least 1  (indentation)
  13:3      warning  missing starting space in comment  (comments)
  13:2      warning  comment not indented like content  (comments-indentation)
  17:1      error    too many blank lines (3 > 0)  (empty-lines)

  server.yml
  1:1       error    too many blank lines (1 > 0)  (empty-lines)
  1:1       error    wrong new line character: expected \n  (new-lines)
  2:1       warning  missing document start "---"  (document-start)
  25:27     error    no new line character at the end of file  (new-line-at-end-of-file)

`Task 06`
In broken block indentation is inconsistent
- docker is not indented under tools:
But - kubernetes is indented.

YAML expects consistent indentation for list items.As below-
tools:
  - docker
  - kubernetes 

DevOps tools (like Kubernetes or GitHub Actions) read YAML to understand configuration.

- If indentation is wrong:
- The tool misunderstands structure
- Required fields may appear missing
- It throws an error