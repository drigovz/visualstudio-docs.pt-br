---
title: Alterações necessárias para projetos do Office migrados para o .NET Framework 4, 4,5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 82ae3f8a43b65e6ff617192dc38149691d229455
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66836065"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Alterações necessárias para executar projetos do Office que você migra para o .NET Framework 4 ou o .NET Framework 4,5
  Se a estrutura de destino de um projeto do Office for alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior de uma versão anterior do .NET Framework, você deverá executar as seguintes tarefas para garantir que a solução possa ser executada no computador de desenvolvimento e nos computadores dos usuários finais:

- Remova o <xref:System.Security.SecurityTransparentAttribute> do projeto se você o tiver atualizado do Visual Studio 2008.

- Execute um comando **limpo** no Visual Studio para poder executar ou depurar o projeto no computador de desenvolvimento.

- Atualize o pré-requisito de .NET Framework para o projeto.

- Os usuários finais também devem reinstalar a solução se você a tiver implantado anteriormente usando o ClickOnce antes de alterar a estrutura de destino.

  Para obter mais informações sobre cada uma dessas tarefas, consulte as seções correspondentes abaixo.

## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Remover o atributo SecurityTransparent dos projetos que você atualiza do Visual Studio 2008
 Se você atualizar um projeto do Office do Visual Studio 2008 e a estrutura de destino do projeto for alterada posteriormente para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deverá remover o <xref:System.Security.SecurityTransparentAttribute> do projeto. O Visual Studio não remove automaticamente esse atributo para você. Se você não remover esse atributo, receberá uma mensagem de erro ao compilar o projeto.

 Para obter mais informações sobre as condições em que o Visual Studio pode alterar a estrutura de destino de um projeto atualizado para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , consulte [atualizar e migrar soluções do Office](../vsto/upgrading-and-migrating-office-solutions.md).

#### <a name="to-remove-the-securitytransparentattribute"></a>Para remover o SecurityTransparentAttribute

1. Com o projeto aberto no Visual Studio, abra **Gerenciador de soluções**.

2. No nó **Propriedades** (para C#) ou no nó **meu projeto** (para Visual Basic), clique duas vezes no arquivo de código AssemblyInfo para abri-lo no editor de códigos.

    > [!NOTE]
    > Em projetos Visual Basic, você deve clicar no botão **Mostrar todos os arquivos** em **Gerenciador de soluções** para ver o arquivo de código AssemblyInfo.

3. Localize o <xref:System.Security.SecurityTransparentAttribute> e remova-o do arquivo ou comente-o.

    ```vb
    <Assembly: SecurityTransparent()>
    ```

    ```csharp
    [assembly: SecurityTransparent()]
    ```

## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Executar o comando de limpeza para depurar ou executar um projeto no computador de desenvolvimento
 Se um projeto do Office foi criado antes de a estrutura de destino do projeto ser alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deve executar um comando **limpo** e recompilar o projeto depois que a estrutura de destino for alterada. Se não executar um comando **limpo** , você receberá um <xref:System.Runtime.InteropServices.COMException> quando tentar depurar ou executar o projeto redirecionado.

 Para obter mais informações sobre o comando **Clean** , consulte [criar soluções do Office](../vsto/building-office-solutions.md).

## <a name="update-the-prerequisites-for-deployment"></a>Atualizar os pré-requisitos para implantação
 Ao redirecionar um projeto do Office para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você também deve atualizar o pré-requisito de .NET Framework correspondente na caixa de diálogo **pré-requisitos** . Caso contrário, a implantação do ClickOnce ou o projeto do InstallShield Limited Edition verificará e instalará uma versão anterior do .NET Framework.

 Para obter mais informações sobre como atualizar os pré-requisitos para implantação em computadores de usuários finais, consulte [como instalar pré-requisitos em computadores de usuários finais para executar soluções do Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).

## <a name="reinstall-solutions-on-end-user-computers"></a>Reinstalar soluções nos computadores dos usuários finais
 Se você usar o ClickOnce para implantar uma solução do Office que tenha como destino o .NET Framework 3,5 e, em seguida, redirecionar o projeto para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, os usuários finais deverão desinstalar a solução e reinstalá-la depois de republicá-la. Se você republicar a solução redirecionada e a solução for atualizada nos computadores dos usuários finais, os usuários finais receberão um <xref:System.Runtime.InteropServices.COMException> quando executarem a solução atualizada.

## <a name="see-also"></a>Confira também
- [Migrar soluções do Office para o .NET Framework 4 ou posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
