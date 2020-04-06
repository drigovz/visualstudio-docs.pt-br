---
title: Função SccProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2dd87efbb50346093144db6e069eea30138e37
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700502"
---
# <a name="sccproperties-function"></a>Função SccProperties
Esta função exibe propriedades de controle de origem para um arquivo ou projeto.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccProperties (
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName
);
```

#### <a name="parameters"></a>parâmetros
 pvContext

[em] A estrutura de contexto plug-in de controle de origem.

 hWnd

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 Lpfilename

[em] O nome do caminho totalmente qualificado do arquivo ou projeto.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|As propriedades foram exibidas com sucesso.|
|SCC_I_RELOADFILE|O sistema de controle de versão modificou as propriedades do arquivo, então o IDE deve recarregar este arquivo.|
|SCC_E_PROJNOTOPEN|O projeto especificado não foi aberto no controle de origem.|
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado a visualizar propriedades deste arquivo ou projeto.|
|SCC_E_FILENOTCONTROLLED|O arquivo ou projeto especificado não está sob controle de origem.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Ocorreu um erro desconhecido ou geral.|

## <a name="remarks"></a>Comentários
 O plug-in de controle de origem exibe as propriedades em sua própria caixa de diálogo.

 As propriedades são definidas pelo plug-in de controle de origem e podem diferir do plug-in para o plug-in. Se o plug-in permitir que o usuário altere as `SCC_I_RELOAD` propriedades de controle de origem de um arquivo, ele deve retornar para sinalizar ao IDE que este arquivo ou projeto precisa ser recarregado.

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
