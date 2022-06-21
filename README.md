<h3> Eloquent Laravel </h3>

<h4> Inserindo dados </h4>

```php
$variavel = new caminho\nome do modelo;

$variavel->coluna01 = 'João';
$variavel->coluna02 = 28;
...
$variavel->colunaN = 21.2;

$variavel->save();
```

<h4> Tabela com nome diferente do modelo </h4>

Para trabalhar com uma table onde o nome está diferente do modelo devemos usar um atributo especial no modelo.

```php

class Fornecedor extends Model
{
  protected $table = 'fornecedores';
}
```

<h4> Inserindo dados sem instância uma classe </h4>

```php
class Fornecedor extends Model
{
    protected $table = 'fornecedores';
    protected $fillable = ['nome', 'uf', 'email'];  // Obrigatório esse atributo com um array das colunas a serem mexidas.
}

App\Models\Fornecedor::create(['nome' => 'Fornecedor 01', 'uf' => 'SP', 'email' => 'fornecedor@email.com']);
```

<h4> Selecionando todos os registros do banco de dados </h4>

```php
use App\Models\Fornecedor
$fornecedor = Fornecedor::all();
```

<h4> Selecionando registros do banco de dados com find() </h4>

```php
use App\Models\Fornecedor
$fornecedor = Fornecedor::find(2);
// retorna o registro com id 2

use App\Models\Fornecedor
$fornecedor = Fornecedor::find([3, 5]);
// retorna o registro com id 3 e 5
```

<h4> Selecionando registros do banco de dados com where() </h4>

```php
use App\Models\SiteContatos
//$contatos = SiteContatos::where('nome_coluna', 'operador_comparacao', 'valor');
$contatos = SiteContatos::where('id', '>', 1)->get();
```

<h4> Modificando dados do banco de dados </h4>

```php
use App\Models\Fornecedor
$fornecedor = Fornecedor::find(1);
$fornecedor->nome = 'João';
$fornecedor->email = 'joao@email.com';
$fornecedor->save();
```

<h4> Deletando registros </h4>

```php
use App\Models\Fornecedor
$fornecedor = Fornecedor::find(1);
$fornecedor->delete();

// modo 02
use App\Models\Fornecedor
Fornecedor::where('id', 7)->delete();

// modo 03
use App\Models\Fornecedor
Fornecedor::destroy(5);
```
