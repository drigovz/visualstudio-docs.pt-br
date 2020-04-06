---
title: Função SccAddFromScc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dd32e31330cdce958e463a40a4d92f88b09afb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701243"
---
# <a name="sccaddfromscc-function"></a>Função SccAddFromScc
Esta função permite que o usuário navegue por arquivos que já estão no sistema de controle de origem e, posteriormente, faça desses arquivos parte do projeto atual. Por exemplo, essa função pode obter um arquivo de cabeçalho comum no projeto atual sem copiar o arquivo. A matriz de `lplpFileNames`retorno de arquivos, contém a lista de arquivos que o usuário deseja adicionar ao projeto IDE.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccAddFromScc (
   LPVOID   pvContext,
   HWND     hWnd,
   LPLONG   lpnFiles,
   LPCSTR** lplpFileNames
);
```

### <a name="parameters"></a>parâmetros
 pvContext

[em] A estrutura de contexto plug-in de controle de origem.

 hWnd

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 lpnFiles

[dentro, fora] Um buffer para o número de arquivos que estão sendo adicionados. (Isto `NULL` é, se `lplpFileNames` a memória apontada por deve ser liberada. Consulte observações para obter detalhes.)

 lplpFileNames

[dentro, fora] Uma matriz de ponteiros para todos os nomes de arquivos sem caminhos de diretório. Esta matriz é alocada e liberada pelo plug-in de controle de origem. Se `lpnFiles` = `lplpFileNames` 1 `NULL`e não for , o `lplpFileNames` primeiro nome na matriz apontada por contém a pasta de destino.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Os arquivos foram localizados com sucesso e adicionados ao projeto.|
|SCC_I_OPERATIONCANCELED|A operação foi cancelada sem efeito.|
|SCC_I_RELOADFILE|Um arquivo ou projeto precisa ser recarregado.|

## <a name="remarks"></a>Comentários
 O IDE chama essa função. Se o plug-in de controle de origem for suportado `lpnFiles` especificando uma pasta de `lplpFileNames`destino local, o IDE será aprovado = 1 e passar o nome da pasta local para .

 Quando a chamada `SccAddFromScc` para a função retorna, o `lpnFiles` plug-in atribui valores e, `lplpFileNames`alocando a memória para o array `lplpFileNames`de nome do arquivo, conforme necessário (observe que essa alocação substitui o ponteiro em ). O plug-in de controle de origem é responsável por colocar todos os arquivos no diretório do usuário ou na pasta de designação especificada. Em seguida, o IDE adiciona os arquivos ao projeto IDE.

 Finalmente, o IDE chama essa função `NULL` uma `lpnFiles`segunda vez, passando para . Isso é interpretado como um sinal especial pelo plug-in de controle de origem para liberar a memória alocada para a matriz de nome de arquivo em`lplpFileNames``.`

 `lplpFileNames`é `char ***` um ponteiro. O plug-in de controle de origem coloca um ponteiro para uma matriz de ponteiros para nomes de arquivos, passando assim a lista da maneira padrão para esta API.

> [!NOTE]
> As versões iniciais da API VSSCI não forneceram uma maneira de indicar o projeto de destino para os arquivos adicionados. Para acomodar isso, a semântica do `lplpFIleNames` parâmetro foi aprimorada para torná-lo um parâmetro de entrar/sair em vez de um parâmetro de saída. Se apenas um único arquivo for especificado, ou `lpnFiles` seja, o valor `lplpFileNames` apontado para = 1, então o primeiro elemento de contém a pasta de destino. Para usar essas novas semânticas, o IDE chama a `SccSetOption` função com o `nOption`parâmetro definido para `SCC_OPT_SHARESUBPROJ`. Se um plug-in de controle de origem não `SCC_E_OPTNOTSUPPORTED`suportar a semântica, ele retorna . Para isso, desativa o uso do recurso **Adicionar do Controle de Origem.** Se um plug-in suportar o recurso`SCC_CAP_ADDFROMSCC`Adicionar do Controle de **Origem** (), `SCC_I_SHARESUBPROJOK`então ele deve suportar a nova semântica e o retorno .

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
