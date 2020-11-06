# Input redirection
`<`

# Output redirection
`>`

# STD
* IN: `0`
* OUT: `1`
* ERR: `2`

# Merge streams
* `n>&m`
	* Merge stdn and stdm
* Example: `2>&1` will redirect stderr to stdout
