---
title: Opções de usuário de solução (. Suo) Arquivo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9469663d3ac258e1c568778894d8584c68c13632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705313"
---
# <a name="solution-user-options-suo-file"></a>Arquivo .Suo (Solution User Options)
O arquivo de opções de usuário de solução (.suo) contém opções de solução por usuário. Este arquivo não deve ser verificado para o controle de código fonte.

 O arquivo de opções de usuário de solução (.suo) é um arquivo de armazenamento estruturado ou composto armazenado em um formato binário. Você salva as informações do usuário em fluxos com o nome do fluxo sendo a chave que será usada para identificar as informações no arquivo .suo. O arquivo de opções de usuário de solução é usado para armazenar as configurações de preferência do usuário e é criado automaticamente quando o Visual Studio salva uma solução.

 Quando o ambiente abre um arquivo .suo, ele enumera todos os VSPackages carregados atualmente. Se um VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> implementar a interface, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> o ambiente chamará o método no VSPackage pedindo-lhe para carregar todos os seus dados do arquivo .suo.

 É responsabilidade do VSPackage saber quais fluxos ele pode ter escrito no arquivo .suo. Para cada fluxo que ele escreveu, o VSPackage chama de volta para o ambiente através <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> de carregar um fluxo específico que é identificado pela chave, que é o nome do fluxo. Em seguida, o ambiente chama de volta para o VSPackage `IStream` para ler <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> esse fluxo em particular passando o nome do fluxo e um ponteiro para o método.

 Nesse ponto, outra chamada `LoadUserOptions` é feita para ver se há outra seção do arquivo .suo que deve ser lida. Esse processo continua até que todos os fluxos de dados do arquivo .suo tenham sido lidos e processados pelo ambiente.

 Quando a solução é salva ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> fechada, o ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> chama o método com um ponteiro para o método. Um `IStream` contendo as informações binárias a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> serem salvas é passado para o método, que `SaveUserOptions` então escreve as informações para o arquivo .suo e chama o método novamente para ver se há outro fluxo de informações para escrever no arquivo .suo.

 Esses dois métodos, `SaveUserOptions` e `WriteUserOptions`, são chamados recursivamente para cada fluxo de informações a serem `IVsSolutionPersistence`salvos no arquivo .suo, passando no ponteiro para . Eles são chamados recursivamente para permitir a escrita de vários fluxos para o arquivo .suo. Dessa forma, as informações do usuário persistem com a solução e é garantido que estará lá na próxima vez que a solução for aberta.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Soluções](../../extensibility/internals/solutions-overview.md)
