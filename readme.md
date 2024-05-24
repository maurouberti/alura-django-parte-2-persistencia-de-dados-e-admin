![Static Badge](https://img.shields.io/badge/Alura-%230b182c)
![Static Badge](https://img.shields.io/badge/Django-4.2.13-%23092E20?logoColor=ffffff)

# 1 - Lidando com dados

Criar **model**  
Alterar arquivo **gaaleria/models.py**

```
class Fotografia(models.Model):
    nome = models.CharField(max_length=100, null=False, blank=False)
    legenda = models.CharField(max_length=150, null=False, blank=False)
    descricao = models.TextField(null=False, blank=False)
    foto = models.CharField(max_length=150, null=False, blank=False)

    def __str__(self):
        return f"Fotografia [nome={self.nome}]"
```

Criar as **migrations**

```
python manage.py makemigrations
```

Executar as migrations

```
python manage.py migrate
```

Alterar arquivo de configuraação **setup/settings.py**
Referenciar configurações específicas da aplicação "galeria"  

```
INSTALLED_APPS = [
    ...
    'galeria.apps.GaleriaConfig',
]
```
