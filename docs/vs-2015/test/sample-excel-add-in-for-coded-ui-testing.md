---
title: Suplemento de exemplo do Excel para testes de IU codificados| Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 18
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6dc6b4385130c6341b5b3545c6c9f71dc67457f5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672190"
---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>Complemento do Excel de amostra para testes de IU codificado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este suplemento de exemplo para [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] foi projetado especificamente para dar suporte a testes de IU codificados de planilhas do Excel que são registrados e executados no Visual Studio Enterprise. O suplemento é criado usando o Visual Studio Tools para Office.

 Para obter mais informações sobre como criar um suplemento do Excel, consulte [Passo a passo: criando o primeiro suplemento do VSTO para Excel](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) ou pesquise o MSDN em busca de "Suplemento do Excel".

 Embora o suplemento do Excel não seja o assunto principal desta documentação da extensão de teste de IU codificado para Excel, alguns comentários podem ser úteis.

 As partes importantes deste suplemento:

- Classe `ThisAddIn` – gerencia o canal de comunicação remota do .NET entre o `ExcelUICommunicator` e a [Extensão de teste de IU codificado de exemplo para Excel](../test/sample-coded-ui-test-extension-for-excel.md).

- `ExcelCodedUIAddinHelper_TemporaryKey.pfx` – um certificado de segurança para testar o suplemento.

- Classe `ExcelUICommunicator` – essa classe implementa a interface `IExcelUICommunication`.

## <a name="thisaddin-class"></a>Classe ThisAddIn
 A maior parte dessa classe, na verdade, é gerada pelo Visual Studio Tools para Office no arquivo `ThisAddIn.Designer.cs` quando você cria o projeto de suplemento do Excel.

 Os membros que você deve implementar são os manipuladores de eventos: `ThisAddIn_Startup()` e `ThisAddIn_Shutdown()`. Sua finalidade é inicializar ou fechar o canal de comunicação remota do .NET que é usado pelo `ExcelUICommunicator`.

## <a name="excelcodeduiaddinhelper_temporarykeypfx"></a>ExcelCodedUIAddinHelper_TemporaryKey.pfx
 Esse arquivo contém um certificado de segurança temporário que é gerado pelo Visual Studio Tools para Office e concederá permissão ao assembly do suplemento para operar no processo do Excel para testar o suplemento e a extensão. Você deve excluir esse certificado e crie um novo na guia **Assinatura** da janela **Propriedades** do projeto ou anexe seu próprio certificado de teste.

## <a name="exceluicommunicator-class"></a>Classe ExcelUICommunicator
 Essa classe implementa a interface `IExcelUITestCommunication` e obtém as informações de interface do usuário solicitadas do modelo de objeto do Excel. Para obter mais informações, consulte [Interface de comunicador do Excel de amostra](../test/sample-excel-communicator-interface.md).

## <a name="see-also"></a>Consulte também
 [Estendendo testes de interface do usuário codificados e gravações de ação para dar suporte ao Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md) [Walkthrough: criando seu primeiro suplemento do VSTO para desenvolvimento do Excel](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) [e do Office](https://msdn.microsoft.com/library/2ddec047-263a-4901-a54c-a15fc8472329)
