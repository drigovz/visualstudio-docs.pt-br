---
title: Função SccGet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2d69308d2f569fc2e0d72dcf64c762687955d4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700895"
---
# <a name="sccget-function"></a>Função SccGet
Esta função recupera uma cópia de um ou mais arquivos para visualização e compilação, mas não para edição. Na maioria dos sistemas, os arquivos são marcados como somente leitura.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccGet(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>parâmetros
 pvContext

[em] A estrutura de contexto do plug-in de controle de origem.

 hWnd

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 nArquivos

[em] Número de arquivos especificados na `lpFileNames` matriz.

 lpFileNames

[em] Matriz de nomes totalmente qualificados de arquivos a serem recuperados.

 fOpções

[em] Bandeiras`SCC_GET_ALL`de `SCC_GET_RECURSIVE`comando ( , ).

 pvOpções

[em] Opções específicas de plug-in de controle de origem.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Sucesso da operação get.|
|SCC_E_FILENOTCONTROLLED|O arquivo não está sob controle de origem.|
|SCC_E_OPNOTSUPPORTED|O sistema de controle de origem não suporta esta operação.|
|SCC_E_FILEISCHECKEDOUT|Não é possível obter o arquivo que o usuário atualmente tem verificado.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção. Recomenda-se uma nova tentativa.|
|SCC_E_NOSPECIFIEDVERSION|Especificado uma versão inválida ou data/hora.|
|SCC_E_NONSPECIFICERROR|Falha não específica; arquivo não foi sincronizado.|
|SCC_I_OPERATIONCANCELED|Operação cancelada antes da conclusão.|
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado a executar essa operação.|

## <a name="remarks"></a>Comentários
 Esta função é chamada com uma contagem e uma matriz de nomes dos arquivos a serem recuperados. Se o IDE `SCC_GET_ALL`passar o sinalizador, isso `lpFileNames` significa que os itens não são arquivos, mas diretórios, e que todos os arquivos sob controle de origem nos diretórios dado devem ser recuperados.

 O `SCC_GET_ALL` sinalizador pode ser `SCC_GET_RECURSIVE` combinado com o sinalizador para recuperar todos os arquivos nos diretórios dado e em todos os subdiretórios também.

> [!NOTE]
> `SCC_GET_RECURSIVE`nunca deve ser `SCC_GET_ALL`passado sem . Além disso, observe que se os diretórios *C:\A* e *C:\A\B* forem repassados em um get recursivo, *C:\A\B* e todos os seus subdiretórios serão recuperados duas vezes. É responsabilidade do IDE — e não do plug-in de controle de origem — garantir que duplicatas como esta sejam mantidas fora da matriz.

 Finalmente, mesmo que um plug-in `SCC_CAP_GET_NOUI` de controle de origem tenha especificado o sinalizador na inicialização, indicando que ele não tem uma interface de usuário para um comando Get, essa função ainda pode ser chamada pelo IDE para recuperar arquivos. O sinalizador simplesmente significa que o IDE não exibe um item do menu Obter e que não se espera que o plug-in forneça qualquer ui.

## <a name="rename-files-and-sccget"></a>Renomear arquivos e SccGet
 Situação: um usuário verifica um arquivo, por exemplo, *a.txt*, e o modifica. Antes *que a.txt* possa ser verificada, um segundo usuário renomeia *a.txt* para *b.txt* no banco de dados de controle de origem, verifica *b.txt,* faz algumas modificações no arquivo e verifica o arquivo. O primeiro usuário quer que as alterações feitas pelo segundo usuário para que o primeiro usuário renomeie sua versão local de um arquivo *a.txt* para *b.txt* e faça um get on the file. No entanto, o cache local que mantém o controle dos números de versão ainda acha que a primeira versão do *a.txt* é armazenada localmente e, portanto, o controle de origem não pode resolver as diferenças.

 Existem duas maneiras de resolver essa situação em que o cache local das versões de controle de origem fica fora de sincronia com o banco de dados de controle de origem:

1. Não permita renomear um arquivo no banco de dados de controle de origem que está atualmente verificado.

2. Faça o equivalente a "excluir velho" seguido de "adicionar novo". O algoritmo a seguir é uma maneira de conseguir isso.

    1. Ligue para a função [SccQueryChanges](../extensibility/sccquerychanges-function.md) para saber sobre a renomeação de *a.txt* para *b.txt* no banco de dados de controle de origem.

    2. Renomeie o *local a.txt* para *b.txt*.

    3. Ligue `SccGet` para a função *para a.txt* e *b.txt*.

    4. Como *o a.txt* não existe no banco de dados de controle de origem, o cache da versão local é eliminado das informações de versão *a.txt* ausentes.

    5. O arquivo *b.txt* que está sendo verificado é mesclado com o conteúdo do arquivo *b.txt* local.

    6. O arquivo *b.txt* atualizado já pode ser conferido.

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags usados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
