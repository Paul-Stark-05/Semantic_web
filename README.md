# Voyager: Maritime Transport Ontology

A Semantic Web project modeling the logistics of maritime passenger transport. This project uses **RDFS** and **OWL** to define a strict hierarchy of passengers, luggage, and transport vessels, ensuring logical consistency through disjoint classes and property restrictions.

## 📌 Ontology Visualization

The following graph illustrates the class hierarchy and property relationships (generated via Corese):

![Ontology Graph](ontology_visualization.png)

## 🛠 Technical Features

* **Language:** Turtle (TTL)
* **Standards:** RDFS, OWL 2 DL
* **Key Constraints:**
    * **Taxonomy:** Clear distinction between `LivingThing`, `InertThing`, and `Passenger` types.
    * **Disjointness:** Strict separation of `AdultPassenger`, `ChildPassenger`, and `AnimalPassenger`.
    * **Functional Logistics:** Modeling travel routes using `owl:FunctionalProperty` for departures and arrivals.

## 📂 File Structure

* `voyager_schema.ttl`: Contains the TBox (Classes, Properties, and Rules).
* `voyager_data.ttl`: Contains the ABox (Instances of the cruise, passengers, and luggage).

## 🚀 Validation & Testing

This ontology has been validated using the **Corese Semantic Web Factory** (developed by WIMMICS).

### Competency Question Execution
*Query: "Which passengers own luggage and how many pieces?"*

```sparql
PREFIX voyager: [http://voyager.cruise/schema#](http://voyager.cruise/schema#)
SELECT ?passenger (COUNT(?luggage) AS ?luggageCount)
WHERE {
    ?passenger voyager:ownsLuggage ?luggage .
}
GROUP BY ?passenger
HAVING (COUNT(?luggage) > 2)
