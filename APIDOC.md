# Nursery API Documentation
*This API provides endpoints to retrieve information about plants in a local nursery. Information is inherently assumed to be stored in server-side directories.*

##
**Request Type:** GET

**Returned Data Format**: JSON

**Description:** Returns a frequently asked question

**Supported Parameters** 
* `number` (required)
  * Index of the frequently asked question. Must be an integer from 1-5.

**Example Request:** GET /question/3

**Example Response:**

```json
{
    "text":"What are the best low-light plants?"
}
```

**Error Handling:**
Returns a 400 level error if the question number is not within the range 1 through 5.

Example: GET /question/8
Output:
```
Invalid question number
```

##
**Request Type:** GET

**Returned Data Format**: JSON

**Description:** Returns the answer to a frequently asked question

**Supported Parameters** 
* `number` (required)
  * Index of the answer to a frequently asked question. Must be an integer from 1-5.

**Example Request:** GET /answer/3

**Example Response:**

```json
{
    "text":"Some of the best low-light plants include snake plants, ZZ plants, and pothos."
}
```

**Error Handling:**
Returns a 400 level error if the answer number is not within the range 1 through 5.

Example: GET /answer/8
Output:
```
Invalid answer number
```

##
**Request Type:** GET

**Returned Data Format**: JSON

**Description:** Returns a current promotion on the website

**Supported Parameters** 
* `number` (required)
  * Index of the promotion. Must be an integer from 1-5.

**Example Request:** GET /promotion/3

**Example Response:**

```json
{
    "text":"Free shipping on orders over $50!"
}
```

**Error Handling:**
Returns a 400 level error if the promotion number is not within the range 1 through 5.

Example: GET /promotion/8
Output:
```
Invalid promotion number
```

##
**Request Type:** GET

**Returned Data Format**: JSON

**Description:** Returns information about all available plants

**Supported Parameters** None

**Example Request:** GET /plant-info

**Example Response:**

```json
{
    "bamboo": [
      "Bamboo is a fast-growing plant that adds a tropical feel to gardens. It prefers well-drained soil and partial shade.",
      30,
      "outdoor"
    ],
    "cactus": [
      "This cactus is perfect for a windowsill and requires minimal watering. It's a great addition to any home or office space.",
      15,
      "indoor"
    ],
    "daffodil": [
      "Daffodils are cheerful yellow flowers that bloom in early spring. They thrive in full sun or partial shade.",
      10,
      "outdoor"
    ],
    "fern": [
      "Ferns are lush, green plants that thrive in shady areas. They require moist, well-drained soil.",
      20,
      "outdoor"
    ],
    "hydrangeas": [
      "Hydrangeas are popular for their large and colorful flower heads. They prefer partial sun and moist soil.",
      25,
      "outdoor"
    ],
    "ivy": [
      "Ivy is a hardy climbing plant that grows well in shady areas. It needs moist, well-drained soil.",
      15,
      "outdoor"
    ],
    "lavender": [
      "Lavender is known for its fragrant purple flowers. It needs full sun and well-drained soil.",
      20,
      "indoor"
    ],
    "lilacs": [
      "Lilacs are known for their beautiful and fragrant flowers. They thrive in well-drained soil and full sunlight.",
      25,
      "indoor"
    ],
    "lily": [
      "Lilies are elegant flowers that come in many colors. They grow best in well-drained soil and full to partial sun.",
      18,
      "indoor"
    ],
    "marigold": [
      "Marigolds are bright, cheerful flowers that repel pests. They thrive in full sun and well-drained soil.",
      10,
      "outdoor"
    ],
    "orchid": [
      "Orchids are exotic plants with unique flowers. They require indirect light and high humidity.",
      35,
      "indoor"
    ],
    "rose": [
      "Roses are classic garden plants with a variety of colors and fragrances. They need full sun and well-drained soil.",
      25,
      "indoor"
    ],
    "sunflower": [
      "Sunflowers are tall and bright, following the sun throughout the day. They need full sun and well-drained soil.",
      15,
      "outdoor"
    ],
    "tulip": [
      "Tulips are spring-blooming perennials with vibrant colors. They prefer full sun and well-drained soil.",
      12,
      "outdoor"
    ],
    "venus": [
      "Venus Fly Traps are fascinating carnivorous plants. They need a humid environment and lots of sunlight.",
      20,
      "indoor"
    ]
  }
  
```

##
**Request Type:** GET

**Returned Data Format**: JSON

**Description:** Returns information about a specific plant

**Supported Parameters** 
* `name` (required)
  * Plant name

**Example Request:** GET /plant-info/cactus

**Example Response:**

```json
{[
  "This cactus is perfect for a windowsill and requires minimal watering. It's a great addition to any home or office space.",
      15,
      "indoor"
]}
```

**Error Handling:**
Returns a 400 level error if the plant name is not a plant supplied by the nursery

Example: GET /plant-info/mint
Output:
```
Invalid plant name
```

##
**Request Type:** GET

**Returned Data Format**: JSON

**Description:** Returns a list of plants that can be in a certain location

**Supported Parameters** 
* `location` (required)
  * Location (outdoor/indoor)

**Example Request:** GET /plant-filter/indoor

**Example Response:**

```json
{
  "items": [
    "cactus",
    "lavender",
    "lilacs",
    "lily",
    "orchid",
    "rose",
    "venus"
  ]
}
```

**Error Handling:**
Returns a 400 level error if the input is not 'indoor' or 'outdoor'

Example: GET /plant-info/spring
Output:
```
Invalid filter, must be 'indoor' or 'outdoor'
```

##
**Request Type:** POST

**Returned Data Format**: text

**Description:** Adds a message to a server-side file

**Supported Parameters** 
* POST body parameters
  * `name` (required) - name
  * `email` (required) - email address
  * `message` (required) - message content

**Example Request:** POST /addMessage 
```json
{
    name : "Jacob",
    email : "jschuste@caltech.edu",
    message : "nice plants!"
}
```

**Example Response:**

```
Request to add Jacob's message to file successfully received!
```

**Error Handling:**
Returns a 500 level error if the output file does not exist

Example: POST /addMessage 
```json
{
    name : "Jacob",
    email : "jschuste@caltech.edu",
    message : "nice plants!"
}
```
Output:
```
server error
```

##
**Request Type:** POST

**Returned Data Format**: text

**Description:** Adds all items in the cart to a file

**Supported Parameters** 
* POST body parameters
  * `plantNames` (required) - list of plants in the cart

**Example Request:** POST /addMessage 
```json
{
    plantNames : ["cactus", "bamboo", "lily"]
}
```

**Example Response:**

```
Order received successfully!
```

**Error Handling:**
Returns a 500 level error if the output file does not exist

Example: POST /addMessage 
```json
{
    plantNames : ["cactus", "bamboo", "lily"]
}
```

Output:
```
server error
```