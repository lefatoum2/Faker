# Faker
## Objectif

Créer de fausses données aléatoires et les enregistrer dans un fichier CSV.


```Python
import pandas as pd
import random

from faker import Faker

faker = Faker('fr_FR')

# Nombre de features
COUNT = 100


def generate_names(count, type):
# Création d'une liste
    item_list = []
    # Mise en place de conditions selon le type de données
    for i in range(count):
        if (type == 'name'):
            c_item = faker.name()
        elif (type == 'address'):
            c_item = faker.address()
        elif (type == 'phone_number'):
            c_item = faker.phone_number()
        elif (type == 'job'):
            c_item = faker.job()

        print(f'[{i}] : {c_item}')
        item_list.append(c_item)

    return item_list


def generate():
    global faker
# génération d'une liste de username, d'adresses, de travail, de numéro de téléphone
    username_list = generate_names(COUNT, 'name')
    address_list = generate_names(COUNT, 'address')
    job_list = generate_names(COUNT, 'job')
    phone_number_list = generate_names(COUNT, 'phone_number')

    data = pd.DataFrame({
        'username': username_list,
        'address': address_list,
        'job': job_list,
        'phone_number': phone_number_list,

    })

    return data


def run():
    data = generate()
    print(data)
    data.to_csv('./users.csv')


if __name__ == '__main__':
    run()

```
## Source
https://faker.readthedocs.io/en/master/
