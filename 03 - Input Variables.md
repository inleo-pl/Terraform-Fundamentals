Usuń środowisko ```aws-dev``` oraz usuń alias ze środowiska ```aws-prod```

UWAGA! Sprawdź, czy nie masz ustawionych zmiennych środowiskowych ```AWS_ACCESS_KEY_ID``` oraz ```AWS_SECRET_ACCESS_KEY```. Sprawdź także czy w swoim katalogu domowym ```$HOME``` nie masz zapisanej komfiguracji AWSCLI w folderze ```.aws```. 

Zmodyfikuj plik konfiguracyjny topologii dodając do niego poniższą sekcję

```
resource "aws_vpc" "vpc" {
  cidr_block = "10.0.0.0/16"
  enable_dns_support   = true
  enable_dns_hostnames = true
  tags = { pod = "POD01" }
}
```

Wydaj polecenie ```terraform plan``` i sprawdź jego rezultat.

Dodaj do konfiguracji providera klucze ```access_key``` oraz ```secret_key``` nadając im wartość ```test```, następnie ponownie wykonaj polecenie ```terraform plan``` i sprawdź jego rezultat.

Zmodyfikuja ```access_key``` oraz ```secret_key``` przypisując im wartości przekazane przez instruktora, następnie ponownie wykonaj polecenie ```terraform plan``` i sprawdź jego rezultat.

Utwórz w głównym folderze projektu nowy plik o nazwie ```variables.tf``` z następujacą zawartością:

```
variable "lab_aws_key" {}
variable "lab_aws_secret" {}
```
Zmodyfikuja także plik z swojego laba przypisując kluczom ```access_key``` oraz ```secret_key``` wartości zadeklarowanych zmiennych. 

```
provider "aws" {
  region  = "eu-central-1"
  access_key = var.lab_aws_key
  secret_key = var.lab_aws_secret
}
```

Wykonaj następnie polecenie ```terraform plan``` i sprawdź jego rezultat.

Wykonaj polecenie ```terraform plan``` z parametrami ```-var``` przekazując odpowiednie wartości zmiennym z linii poleceń

Utwórz w głównym folderze projektu plik o nazwie ```terraform.tfvars``` o następującej zawartości:
```
lab_aws_key = "test"
lab_aws_secret = "test"
```
Wykonaj następnie polecenie ```terraform plan``` i sprawdź jego rezultat.

Zmodyfikuj wartości zmiennych zapisane w pliku ```terraform.tfvars``` podając wartości przekazane przez instruktora, następnie ponownie wykonaj polecenie ```terraform plan``` i sprawdź jego wynik.
