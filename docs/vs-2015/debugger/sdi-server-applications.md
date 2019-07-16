---
title: Aplicativos de servidor SDI | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1296c0f43d0409df0081861095c5ec068932bbc1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148156"
---
# <a name="sdi-server-applications"></a>Aplicativos de servidor SDI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se estiver depurando um aplicativo para servidores de SDI, especifique `/Embedding` ou `/Automation` na propriedade **Argumentos de linha de comando** na caixa de diálogo Páginas de Propriedades de *Projeto* de projetos C/C++, C# ou do Visual Basic.  
  
 Com esses argumentos de linha de comando, o depurador pode iniciar o aplicativo de servidor como se tivesse sido iniciado de um contêiner. Iniciar o contêiner do Gerenciador de Programas ou do Gerenciador de Arquivos fará com que o contêiner use a instância do servidor iniciada no depurador.  
  
## <a name="finding-the-command-line-arguments-property"></a>Localizando a propriedade Argumentos de Linha de Comando  
 Para acessar a caixa de diálogo Páginas de Propriedades de *Projeto*, clique com o botão direito do mouse no projeto no Gerenciador de Soluções e escolha Propriedades no menu de atalho. Para localizar a propriedade Argumentos de linha de comando, expanda a categoria Propriedades de Configuração e clique na página Depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração de COM e ActiveX](../debugger/com-and-activex-debugging.md)   
 [Como: Depurar servidores COM](../debugger/how-to-debug-com-servers.md)
