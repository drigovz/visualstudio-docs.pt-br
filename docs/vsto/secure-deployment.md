---
title: Implantação segura
description: Saiba como você deve fornecer evidências sobre a qual basear uma decisão de confiança assinando a solução com um certificado ou usando a chave de prompt de confiança do ClickOnce.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b47a18aa3e791d446abc2a57b6aad1f139924ebf
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528463"
---
# <a name="secure-deployment"></a>Implantação segura
  Quando você cria uma solução do Office, seu computador de desenvolvimento é atualizado automaticamente para permitir que o código em seu projeto seja executado. No entanto, ao implantar sua solução, você deve fornecer evidências nas quais basear uma decisão de confiança assinando a solução com um certificado ou usando a [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chave de prompt de confiança. Para obter mais informações, consulte [Grant Trust to Office Solutions](../vsto/granting-trust-to-office-solutions.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Para personalizações em nível de documento, se você implantar o documento em um local de rede, também deverá adicionar o local do documento à lista de locais confiáveis na central de confiabilidade do aplicativo do Office. Para obter mais informações sobre como definir permissões de documento em computadores de usuários finais, consulte [conceder confiança a documentos](../vsto/granting-trust-to-documents.md).

## <a name="prevent-office-solutions-from-running-code"></a>Impedir que as soluções do Office executem código
 Os administradores podem usar o registro para impedir que todas as soluções do Office sejam executadas em um computador. Quando uma solução do Office que tem extensões de código gerenciado é aberta, o Ferramentas do Visual Studio para o tempo de execução do Office verifica se existe uma entrada com o nome `Disabled` em uma das seguintes chaves do registro no computador:

- **HKEY_CURRENT_USER\Software\Microsoft\VSTO**

- **HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO**

  Para impedir que as soluções do Office executem código, crie uma `Disabled` entrada em uma ou ambas as chaves do registro e especifique um dos seguintes tipos de dados e valores para `Disabled` :

- Uma REG_SZ ou REG_EXPAND_SZ que é definida como qualquer cadeia de caracteres diferente de "0" (zero).

- Uma REG_DWORD que é definida para qualquer valor diferente de 0 (zero).

  Para permitir que as soluções do Office executem o código, defina as duas `Disabled` entradas como 0 (zero) ou exclua as entradas do registro.

## <a name="see-also"></a>Veja também
- [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)
- [Preparar computadores para executar ou hospedar soluções do Office](/previous-versions/bb772092(v=vs.110))
- [Proteger soluções do Office](../vsto/securing-office-solutions.md)