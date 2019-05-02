---
title: A cadeia de caracteres de conexão contém credenciais com uma senha de texto não criptografado e não está usando segurança integrada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3b75c4e7cf1b1d0374c9ff648861e049aca988c4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424955"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>A cadeia de conexão contém credenciais com uma senha de texto não criptografado e não estiver usando segurança integrada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Deseja salvar a cadeia de conexão no arquivo DBML atual e nos arquivos de configuração do aplicativo com essas informações confidenciais?  Clique em Não para salvar a cadeia de conexão sem as informações confidenciais.  
  
 Ao trabalhar com conexões de dados que incluem informações confidenciais (senhas que são incluídas na cadeia de conexão), você tem a opção de salvar a cadeia de conexão no arquivo DBML de um projeto e o arquivo de configuração do aplicativo com ou sem informações sigilosas.  
  
> [!WARNING]
> Explicitamente definindo a propriedade de **Configurações do Aplicativo** propriedades de **Conexão** a **False** adicionará a senha para o arquivo DBML.  
  
### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>Para salvar a cadeia de conexão com informações sigilosas nas configurações de aplicativo do projeto  
  
- Clique em **Sim**.  
  
     A cadeia de conexão é armazenada como uma configuração de aplicativo. A cadeia de conexão inclui informações sigilosas em texto sem formatação. O arquivo DBML não contém informações sigilosas.  
  
### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>Para salvar a cadeia de conexão sem informações sigilosas nas configurações de aplicativo do projeto  
  
- Clique em **Não**.  
  
     A cadeia de conexão é armazenada como uma configuração de aplicativo, mas a senha não é incluído.  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
