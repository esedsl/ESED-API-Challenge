# ESED API Challenge

The aim of the challenge is to prove the capabilities of the applicant to develop a solution to aggregate data from 3 apis (or more) and return the result in a single endpoint using a local webserver.

# Endpoints
* https://aggregation-challenge.esedsl.com/v1
* https://aggregation-challenge.esedsl.com/v2
* https://aggregation-challenge.esedsl.com/v3

These apis return data in json format, with different structures but based on the same dataset.

The apis may fail (http error 500) or be slow, so the solution must be resilient to this kind of situations.

v1, v2, and v3, differ their return data in the following way:
# Endpoints versions:
## v1:
```
{
    "name": "OA_pu3",
    "path": "custom/OA/content",
    "tag": "OA",
    "weight": "0.25758766588494697",
    "weight_unit": "microlitres"
}
```
## v2:
```
{
    "name": "OA_pu3",
    "path": "custom/OA/content",
    "category": "OA",
    "weight" :0.25758766588494697,
    "weight_unit": "microlitres"
}
```

## v3:
```
{
    "name": "OA_pu3",
    "path": "custom/OA/content",
    "mass": 0.25758766588494697,
    "mass_unit": "microlitres",
    "family": "OA",
    "user": "A.T"
}
```

# Normalizing the results
v3 is the most complete and normalized version of the data, so the solution must return the data in this format.

## Family
The `family` field is the last version of the `tag` and `category` field, so the solution must return the family field in the response.
## User field
v3 includes a new field, `user`, which is not present in v1 and v2. This field must be filled with the value "anonymous".
