---
title: Implantação segura
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1000504ad83706bd028af4bd668da7483e478b7a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978353"
---
# <a name="secure-deployment"></a>Implantação segura
  Quando você cria uma solução do Office, seu computador de desenvolvimento é atualizado automaticamente para permitir que o código em seu projeto para ser executado. No entanto, quando você implanta sua solução, você deve fornecer a evidência na qual basear uma decisão de confiança da solução com um certificado de assinatura, ou usando o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chave prompt de confiança. Para obter mais informações, consulte [conceder confiança a soluções do Office](../vsto/granting-trust-to-office-solutions.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Para personalizações no nível do documento, se você implantar o documento em um local de rede, você deve também adicionar a localização do documento à lista de locais confiáveis na Central de confiabilidade do aplicativo do Office. Para obter mais informações sobre como definir permissões de documento nos computadores dos usuários finais, consulte [conceder confiança a documentos](../vsto/granting-trust-to-documents.md).

## <a name="prevent-office-solutions-from-running-code"></a>Impedir a execução de código de soluções do Office
 Os administradores podem usar o registro para impedir que todas as soluções do Office em execução em um computador. Quando uma solução do Office que tem extensões de código gerenciado é aberto, o Visual Studio Tools para verificações de tempo de execução do Office se uma entrada com o nome `Disabled` existe em uma das seguintes chaves do registro no computador:

- **HKEY_CURRENT_USER\Software\Microsoft\VSTO**

- **HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO**

  Para impedir a execução de código de soluções do Office, crie uma `Disabled` entrada em uma ou ambas as chaves do registro e especifique um dos seguintes tipos de dados e valores para `Disabled`:

- Um REG_SZ ou REG_EXPAND_SZ é definido como qualquer cadeia de caracteres diferente de "0" (zero).

- REG_DWORD que é definido como qualquer valor diferente de 0 (zero).

  Para habilitar soluções do Office para executar o código, defina ambos o `Disabled` entradas como 0 (zero), ou excluir as entradas do registro.

## <a name="see-also"></a>Consulte também
- [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)
- [Preparar os computadores para executar ou hospedar soluções do Office](https://msdn.microsoft.com/be1b173f-7261-4d74-aa4e-94ccd43db8d8)
- [Proteger as soluções do Office](../vsto/securing-office-solutions.md)
