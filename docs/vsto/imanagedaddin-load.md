---
title: IManagedAddin::Load
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 605c1dc7a7b0d24ba082767930fd53148cccbd95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920327"
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Chamado quando um suplemento do VSTO gerenciado é carregado.

## <a name="syntax"></a>Sintaxe

```csharp
HRESULT Load([in] BSTR bstrManifestURL,
             [in] IDispatch *pdispApplication);
```

### <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|
|---------------|-----------------|
|*bstrManifestURL*|O caminho completo do manifesto para o suplemento do VSTO.|
|*pdispApplication*|Um ponteiro para um IDispatch que representa o aplicativo host que está carregando o suplemento do VSTO.|

## <a name="return-value"></a>Valor retornado
 Um valor HRESULT que indica se o método foi concluído com êxito.

## <a name="remarks"></a>Comentários
 Um manifesto é um arquivo (normalmente, um arquivo XML) que fornece informações que são usadas para ajudar a carregar o suplemento do VSTO. Por exemplo, um manifesto pode especificar o local do assembly do suplemento do VSTO e a classe do ponto de entrada para instanciar quando o suplemento do VSTO for carregado.

 O parâmetro *bstrManifestURL* contém o valor da `Manifest` entrada na chave do registro **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<application name>_ \Addins \\ _\<add-in ID>_** para o suplemento do VSTO. Para obter mais informações, consulte [interface IManagedAddin](../vsto/imanagedaddin-interface.md).

 Implemente o método [IManagedAddin:: Load](../vsto/imanagedaddin-load.md) para executar tarefas como configurar o domínio do aplicativo e a política de segurança para o suplemento do VSTO que está sendo carregado.

## <a name="see-also"></a>Consulte também
- [Interface IManagedAddin](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
