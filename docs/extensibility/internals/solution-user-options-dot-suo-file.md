---
title: Opções de usuário da solução (. Arquivo suo) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f529a3861ed6061b428818140ad90d6ca79991af
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56600861"
---
# <a name="solution-user-options-suo-file"></a>Arquivo .Suo (Solution User Options)
O arquivo de opções (. suo) do usuário de solução contém opções de solução por usuário. Esse arquivo não deve ser verificado controle do código fonte.

 O arquivo de opções (. suo) do usuário de solução é um armazenamento estruturado ou composto, um arquivo armazenado em um formato binário. Você pode salvar informações do usuário em fluxos com o nome do fluxo que está sendo a chave que será usada para identificar as informações no arquivo. suo. O arquivo de opções de usuário da solução é usado para armazenar as configurações de preferência do usuário e é criado automaticamente quando o Visual Studio salva uma solução.

 Quando o ambiente de abre um arquivo. suo, ele enumera todos os VSPackages atualmente carregados. Se um VSPackage implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interface e, em seguida, as chamadas de ambiente a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> método em um VSPackage solicitando que ele carregar todos os seus dados do arquivo. suo.

 É responsabilidade do VSPackage saber o que ele transmite talvez tenha gravado no arquivo. suo. Para cada fluxo que ele escreveu, o VSPackage chama de volta para o ambiente por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> para carregar um fluxo específico que é identificado pela chave, que é o nome do fluxo. O ambiente, em seguida, chama de volta para o VSPackage ler esse fluxo específico passando o nome do fluxo e um `IStream` ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> método.

 Nesse ponto, outra chamada é feita para `LoadUserOptions` para ver se há outra seção do arquivo. suo que deve ser lidos. Esse processo continua até que todos os fluxos de dados no arquivo. suo são lidos e processados pelo ambiente.

 Quando a solução é salvo ou fechada, o ambiente chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> método com um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> método. Uma `IStream` que contém as informações de binárias a ser salvo é passado para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> método, que, em seguida, grava as informações de arquivo. suo e chama o `SaveUserOptions` método novamente para ver se há outro fluxo de informações para gravar a. suo arquivo.

 Esses dois métodos, `SaveUserOptions` e `WriteUserOptions`, são chamados recursivamente para cada fluxo de informações a serem salvas no arquivo. suo, passando o ponteiro para `IVsSolutionPersistence`. Eles são chamados de forma recursiva para permitir a gravação de vários fluxos para o arquivo. suo. Dessa forma, as informações do usuário são mantidas com a solução e é garantido que seja lá na próxima vez em que a solução for aberta.

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Soluções](../../extensibility/internals/solutions.md)