Stwórz projekt a w nim dodaj plik ```lab.tf``` i zadeklaruj w nim providera AWS
```
provider "aws" {
  region  = "eu-central-1"
}
```
Wydaj polecenie ```terraform init``` i sprawdź czy poprawnie się zainicjowała struktura projektu.

Rozbuduj konfigurację definiując dwóch providerów AWS

```
provider "aws" {
  region  = "eu-central-1"
  alias = "aws-prod"
}

provider "aws" {
  region  = "eu-west-1"
  alias = "aws-dev"
}
```

Skasuj utworzone poprzednio środowisko i ponownie je zainicjuj.

Dla środowiska ```aws-dev``` wymuś providera w wersji 2.68.0
```
provider "aws" {
  region  = "eu-west-1"
  alias = "aws-dev"
  version = "2.68.0"
}
```
Sprawdź zawartość folderu ```.terraform``` w katalogu roboczym projektu.
