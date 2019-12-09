---
title: Opções de usuário da solução (. Suo) arquivo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f21e4a4a6530692709247e64b0d84aa7b06eb3a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723807"
---
# <a name="solution-user-options-suo-file"></a>Arquivo .Suo (Solution User Options)
O arquivo de opções de usuário da solução (. suo) contém opções de solução por usuário. Esse arquivo não deve ser verificado no controle do código-fonte.

 O arquivo de opções de usuário da solução (. suo) é um arquivo de armazenamento estruturado ou composto, armazenado em um formato binário. Você salva as informações do usuário em fluxos com o nome do fluxo sendo a chave que será usada para identificar as informações no arquivo. suo. O arquivo de opções de usuário da solução é usado para armazenar as configurações de preferência do usuário e é criado automaticamente quando o Visual Studio salva uma solução.

 Quando o ambiente abre um arquivo. suo, ele enumera todos os VSPackages carregados no momento. Se um VSPackage implementar a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>, o ambiente chamará o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> no VSPackage solicitando que ele carregue todos os seus dados do arquivo. suo.

 É responsabilidade do VSPackage saber quais fluxos podem ter sido gravados no arquivo. suo. Para cada fluxo que ele escreveu, o VSPackage chama de volta para o ambiente por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> carregar um fluxo específico que é identificado pela chave, que é o nome do fluxo. Em seguida, o ambiente chama de volta para o VSPackage para ler esse fluxo específico passando o nome do fluxo e um ponteiro de `IStream` para o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>.

 Nesse ponto, outra chamada é feita para `LoadUserOptions` para ver se há outra seção do arquivo. suo que deve ser lida. Esse processo continua até que todos os fluxos de dados no arquivo. suo tenham sido lidos e processados pelo ambiente.

 Quando a solução é salva ou fechada, o ambiente chama o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> com um ponteiro para o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A>. Um `IStream` que contém as informações binárias a serem salvas é passado para o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A>, que, em seguida, grava as informações no arquivo. suo e chama o método `SaveUserOptions` novamente para ver se há outro fluxo de informações a ser gravado no arquivo. suo.

 Esses dois métodos, `SaveUserOptions` e `WriteUserOptions`, são chamados recursivamente para cada fluxo de informações a ser salvo no arquivo. suo, passando o ponteiro para `IVsSolutionPersistence`. Eles são chamados recursivamente para permitir a gravação de vários fluxos no arquivo. suo. Dessa forma, as informações do usuário são mantidas com a solução e há garantia de que estejam lá na próxima vez em que a solução for aberta.

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Soluções](../../extensibility/internals/solutions-overview.md)