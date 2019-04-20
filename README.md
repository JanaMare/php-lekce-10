# Lekce 10

> Večerní kurz programování v PHP

* Vazby mezi entitami
  * Many to one
  * One to many
  * Many to many

## Postup řešení prvního úkolu

* Spustit SSH session
* Přepnout se do složky s aktuální lekcí:
```
cd html/php-lekce-10
```
* Vygenerovat relaci ManyToOne v třídě `Product`:
```
php bin/console make:entity

 Class name of the entity to create or update (e.g. AgreeablePizza):
 > Product

 Your entity already exists! So let's add some new fields!

 New property name (press <return> to stop adding fields):
 > manufacturer

 Field type (enter ? to see all types) [string]:
 > relation

 What class should this entity be related to?:
 > Manufacturer

 Relation type? [ManyToOne, OneToMany, ManyToMany, OneToOne]:
 > ManyToOne

 Is the Product.manufacturer property allowed to be null (nullable)? (yes/no) [yes]:
 > yes

 Do you want to add a new property to Manufacturer ...? (yes/no) [yes]:
 > yes
 
 New field name inside Manufacturer [products]:
 > products

 Add another property? Enter the property name (or press <return> to stop adding fields):
 > 
 
 Success! 
```
* Aktualizovat databázi:
```
php bin/console doctrine:schema:update --force
```
* Stáhnout změněné soubory (složku `src/Entity`) z serveru


## Postup řešení druhého úkolu

* Spustit SSH session a přepnout se do složky s aktuální lekcí (nebo pokračovat v terminálu z minulého úkolu)
* Vygenerovat relaci ManyToMany v třídě `Product`:
```
php bin/console make:entity

 Class name of the entity to create or update (e.g. BraveGnome):
 > Product

 Your entity already exists! So let's add some new fields!

 New property name (press <return> to stop adding fields):
 > suppliers

 Field type (enter ? to see all types) [string]:
 > relation

 What class should this entity be related to?:
 > Supplier

 Relation type? [ManyToOne, OneToMany, ManyToMany, OneToOne]:
 > ManyToMany

 Do you want to add a new property to Supplier so that you can access/update Product objects from it - e.g. $supplier->getProducts()? (yes/no) [yes]:
 > 

 A new property will also be added to the Supplier class so that you can access the related Product objects from it.

 New field name inside Supplier [products]:
 > 

 updated: src/Entity/Product.php
 updated: src/Entity/Supplier.php

 Add another property? Enter the property name (or press <return> to stop adding fields):
 > 

 Success! 
```
* Aktualizovat databázi:
```
php bin/console doctrine:schema:update --force
```
* Stáhnout změněné soubory (složku `src/Entity`) z serveru
