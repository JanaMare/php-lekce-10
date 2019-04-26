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


## Postup řešení domácího úkolu

**Bod 1:** Entita `Sex`:
```
www-data@1edf3f5afb71:~/html/php-lekce-10$ php bin/console make:entity

 Class name of the entity to create or update (e.g. GentleElephant):
 > Sex

 created: src/Entity/Sex.php
 created: src/Repository/SexRepository.php
 
 Entity generated! Now let's add some fields!
 You can always add more fields later manually or by re-running this command.

 New property name (press <return> to stop adding fields):
 > name

 Field type (enter ? to see all types) [string]:
 > 

 Field length [255]:
 > 

 Can this field be null in the database (nullable) (yes/no) [no]:
 > 

 updated: src/Entity/Sex.php

 Add another property? Enter the property name (or press <return> to stop adding fields):
 > 


           
  Success! 
           


```

**Bod 2:** Entita `Person`:
```
www-data@1edf3f5afb71:~/html/php-lekce-10$ php bin/console make:entity

 Class name of the entity to create or update (e.g. AgreeableElephant):
 > Person

 created: src/Entity/Person.php
 created: src/Repository/PersonRepository.php
 
 Entity generated! Now let's add some fields!
 You can always add more fields later manually or by re-running this command.

 New property name (press <return> to stop adding fields):
 > name

 Field type (enter ? to see all types) [string]:
 > 

 Field length [255]:
 > 

 Can this field be null in the database (nullable) (yes/no) [no]:
 > 

 updated: src/Entity/Person.php

 Add another property? Enter the property name (or press <return> to stop adding fields):
 > sex

 Field type (enter ? to see all types) [string]:
 > relation

 What class should this entity be related to?:
 > Sex

What type of relationship is this?
 ------------ ------------------------------------------------------------ 
  Type         Description                                                 
 ------------ ------------------------------------------------------------ 
  ManyToOne    Each Person relates to (has) one Sex.                       
               Each Sex can relate/has to (have) many Person objects       
                                                                           
  OneToMany    Each Person relates can relate to (have) many Sex objects.  
               Each Sex relates to (has) one Person                        
                                                                           
  ManyToMany   Each Person relates can relate to (have) many Sex objects.  
               Each Sex can also relate to (have) many Person objects      
                                                                           
  OneToOne     Each Person relates to (has) exactly one Sex.               
               Each Sex also relates to (has) exactly one Person.          
 ------------ ------------------------------------------------------------ 

 Relation type? [ManyToOne, OneToMany, ManyToMany, OneToOne]:
 > ManyToOne

 Is the Person.sex property allowed to be null (nullable)? (yes/no) [yes]:
 > no

 Do you want to add a new property to Sex so that you can access/update Person objects from it - e.g. $sex->getPeople()? (yes/no) [yes]:
 > 

 A new property will also be added to the Sex class so that you can access the related Person objects from it.

 New field name inside Sex [people]:
 > 

 Do you want to activate orphanRemoval on your relationship?
 A Person is "orphaned" when it is removed from its related Sex.
 e.g. $sex->removePerson($person)
 
 NOTE: If a Person may *change* from one Sex to another, answer "no".

 Do you want to automatically delete orphaned App\Entity\Person objects (orphanRemoval)? (yes/no) [no]:
 > 

 updated: src/Entity/Person.php
 updated: src/Entity/Sex.php

 Add another property? Enter the property name (or press <return> to stop adding fields):
 > age

 Field type (enter ? to see all types) [string]:
 > integer

 Can this field be null in the database (nullable) (yes/no) [no]:
 > 

 updated: src/Entity/Person.php

 Add another property? Enter the property name (or press <return> to stop adding fields):
 > 


           
  Success! 
           

```

**Bod 3:** Otec a matka v `Person`:
```
www-data@1edf3f5afb71:~/html/php-lekce-10$ php bin/console make:entity

 Class name of the entity to create or update (e.g. BraveGnome):
 > Person

 Your entity already exists! So let's add some new fields!

 New property name (press <return> to stop adding fields):
 > father

 Field type (enter ? to see all types) [string]:
 > relation

 What class should this entity be related to?:
 > Person

What type of relationship is this?
 ------------ --------------------------------------------------------------- 
  Type         Description                                                    
 ------------ --------------------------------------------------------------- 
  ManyToOne    Each Person relates to (has) one Person.                       
               Each Person can relate/has to (have) many Person objects       
                                                                              
  OneToMany    Each Person relates can relate to (have) many Person objects.  
               Each Person relates to (has) one Person                        
                                                                              
  ManyToMany   Each Person relates can relate to (have) many Person objects.  
               Each Person can also relate to (have) many Person objects      
                                                                              
  OneToOne     Each Person relates to (has) exactly one Person.               
               Each Person also relates to (has) exactly one Person.          
 ------------ --------------------------------------------------------------- 

 Relation type? [ManyToOne, OneToMany, ManyToMany, OneToOne]:
 > ManyToOne

 Is the Person.father property allowed to be null (nullable)? (yes/no) [yes]:
 > 

 Do you want to add a new property to Person so that you can access/update Person objects from it - e.g. $person->getPeople()? (yes/no) [yes]:
 > 

 A new property will also be added to the Person class so that you can access the related Person objects from it.

 New field name inside Person [people]:
 > fathersCildren

 updated: src/Entity/Person.php

 Add another property? Enter the property name (or press <return> to stop adding fields):
 > mother

 Field type (enter ? to see all types) [string]:
 > relation

 What class should this entity be related to?:
 > Person

What type of relationship is this?
 ------------ --------------------------------------------------------------- 
  Type         Description                                                    
 ------------ --------------------------------------------------------------- 
  ManyToOne    Each Person relates to (has) one Person.                       
               Each Person can relate/has to (have) many Person objects       
                                                                              
  OneToMany    Each Person relates can relate to (have) many Person objects.  
               Each Person relates to (has) one Person                        
                                                                              
  ManyToMany   Each Person relates can relate to (have) many Person objects.  
               Each Person can also relate to (have) many Person objects      
                                                                              
  OneToOne     Each Person relates to (has) exactly one Person.               
               Each Person also relates to (has) exactly one Person.          
 ------------ --------------------------------------------------------------- 

 Relation type? [ManyToOne, OneToMany, ManyToMany, OneToOne]:
 > ManyToOne

 Is the Person.mother property allowed to be null (nullable)? (yes/no) [yes]:
 > 

 Do you want to add a new property to Person so that you can access/update Person objects from it - e.g. $person->getPeople()? (yes/no) [yes]:
 > 

 A new property will also be added to the Person class so that you can access the related Person objects from it.

 New field name inside Person [people]:
 > mothersChildren

 updated: src/Entity/Person.php

 Add another property? Enter the property name (or press <return> to stop adding fields):
 > 


           
  Success! 
           

```

Nyní je třeba provést změny v databázi (budou smazána všechna data!):
```
php bin/console doctrine:database:drop --force
php bin/console doctrine:database:create
php bin/console doctrine:schema:update --force
```

**Bod 4:** Vytvořit CRUD pro `Preson`:
```
www-data@1edf3f5afb71:~/html/php-lekce-10$ php bin/console make:crud

 The class name of the entity to create CRUD (e.g. GrumpyJellybean):
 > Person

 created: src/Controller/PersonController.php
 created: src/Form/PersonType.php
 created: templates/person/_delete_form.html.twig
 created: templates/person/_form.html.twig
 created: templates/person/edit.html.twig
 created: templates/person/index.html.twig
 created: templates/person/new.html.twig
 created: templates/person/show.html.twig

           
  Success! 
           
```

Nyní je třeba udělat ručně změny v  `src/Form/PersonType.php`

**Bod 5:** Zobrazit děti v detailu osoby -> úprava šablony `templates/person/show.html.twig`

**Bod 6:** Přidat validace do třídy `App\Entity\Person` -> nová metoda `validate`
