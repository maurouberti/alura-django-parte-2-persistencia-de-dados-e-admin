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

# 2 - Admin

Alterar arquivo **galeria/views.py**  
Passar as fotografias para o **templates/galeria/index.html**

```
def index(request):
    fotografias = Fotografia.objects.all()
    return render(request, 'galeria/index.html', {"cards": fotografias})
```

Colocar comando `for` nos cards do **templates/galeria/index.html**

```
{% for fotografia in cards %}
...
{% endfor %}
```

## Admin

Criar usuário

```
python manage.py createsuperuser
```

Acessar

```
http://127.0.0.1:8000/admin
```

Habilitar model Fotograrfia no admin.  
Alterar arquivo **galeria/admin.py**

```
from galeria.models import Fotografia
admin.site.register(Fotografia)
```

Adicionar configurações no grid

```
class ListandoFotografias(admin.ModelAdmin):
    list_display = ("id", "nome", "legenda")
    list_display_links = ("id","nome")
    search_fields = ("nome",)
```
