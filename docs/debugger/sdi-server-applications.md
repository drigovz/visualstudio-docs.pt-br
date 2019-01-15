---
title: Aplicativos de servidor SDI | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec4178fb23d84812d7258bac8384264bed9d4690
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53885044"
---
# <a name="sdi-server-applications"></a>Aplicativos de servidor SDI
Se estiver depurando um aplicativo para servidores de SDI, especifique `/Embedding` ou `/Automation` na propriedade **Argumentos de linha de comando** na caixa de diálogo Páginas de Propriedades de *Projeto* de projetos C/C++, C# ou do Visual Basic.  
  
 Com esses argumentos de linha de comando, o depurador pode iniciar o aplicativo de servidor como se tivesse sido iniciado de um contêiner. Iniciar o contêiner do Gerenciador de Programas ou do Gerenciador de Arquivos fará com que o contêiner use a instância do servidor iniciada no depurador.  
  
## <a name="finding-the-command-line-arguments-property"></a>Localizando a propriedade Argumentos de Linha de Comando  
 Para acessar a caixa de diálogo Páginas de Propriedades de *Projeto*, clique com o botão direito do mouse no projeto no Gerenciador de Soluções e escolha Propriedades no menu de atalho. Para localizar a propriedade Argumentos de linha de comando, expanda a categoria Propriedades de Configuração e clique na página Depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração de COM e ActiveX](../debugger/com-and-activex-debugging.md)   
 [Como: Depurar servidores COM](../debugger/how-to-debug-com-servers.md)