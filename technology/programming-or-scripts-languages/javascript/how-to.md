# How to

## Install ESLint

```text
npm uninstall -g eslint
npm i eslint --save-dev
./node_modules/.bin/eslint --init
```

## Validate a group of conditions

```text
let conditionsArray = [ condition1, condition2, condition3, ]

if (conditionsArray.indexOf(false) === -1) { "do somthing" }
```

## Oliver Steele’s Nested Object Access Pattern

```text
const name = ((user || {}).personalInfo || {}).name;
```

## Download files with Axios and Laravel

* Javascript

```text
export const getFile = (coArquivo, config = { responseType: 'blob' }) => instance.get(`/upload/${coArquivo}`, config)
  .then((response) => {
    const { headers } = response;
    const dadosFilename = headers['content-disposition'].split('filename=');
    const filename = dadosFilename[1];
  
    const url = window.URL.createObjectURL(new Blob([response.data]));
    const link = document.createElement('a');
    link.href = url;
    link.setAttribute('download', filename);
    document.body.appendChild(link);
    link.click();
  });
```

* Laravel: cors.php

```text
<?php

return [

    /*
    |--------------------------------------------------------------------------
    | Laravel CORS
    |--------------------------------------------------------------------------
    |
    | allowedOrigins, allowedHeaders and allowedMethods can be set to array('*')
    | to accept any value.
    |
    */

    'supportsCredentials' => false,
    'allowedOrigins' => ['*'],
    'allowedOriginsPatterns' => [],
    'allowedHeaders' => ['*'],
    'allowedMethods' => ['*'],
    'exposedHeaders' => ['Content-Disposition'],
    'maxAge' => 0,

];
```

* Laravel: Controller

```text
class UploadController extends Controller
{

    protected $service;

    public function __construct(UploadService $service)
    {
        $this->service = $service;
        $this->middleware('auth:api');
    }


    public function show($identificador)
    {
        return $this->service->downloadArquivo((int) $identificador);
    }
}
```

```text
...
public function downloadArquivo($identificador)
    {
        $arquivo = $this->_obterArquivo($identificador);
        if (empty($arquivo)) {
            throw new EParametrosInvalidos("O arquivo solicitado não existe.");
        }
        return Storage::download($arquivo->ds_localizacao, $arquivo->no_arquivo);
    }
```

## Get only decimal from number 

```text
const number = 11,12;
Math.round((number + Number.EPSILON) * 100) / 100
```

