---
title: Proteção de documentos em soluções de nível de documento
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6c5f019907495c3cad3fddef501455aedf345bb2
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253802"
---
# <a name="document-protection-in-document-level-solutions"></a>Proteção de documentos em soluções de nível de documento
  Você pode usar os recursos de proteção do Microsoft Office Word e Microsoft Office Excel em projetos de nível de documento. Esses recursos impedem que usuários não autorizados façam alterações em partes protegidas de um documento.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Usando o Excel, você pode ativar e desativar a proteção enquanto a pasta de trabalho está aberta no designer. Usando o Word, você pode ativar a proteção somente fora do designer. Em tempo de execução, você pode habilitar ou desabilitar a proteção programaticamente para o Word e o Excel.

 Quando a proteção de documentos está habilitada em um documento aberto no designer, todos os controles são removidos da **caixa de ferramentas** ou ficam indisponíveis, e você não pode arrastar nada da janela **fontes de dados** para o documento.

## <a name="serverdocument-and-protected-documents"></a>ServerDocument e documentos protegidos
 Se um documento estiver protegido, o cache de dados não poderá ser acessado de fora do documento. Você não pode usar <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> a classe para recuperar ou manipular dados armazenados em cache em um documento protegido ou usar outros métodos <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> da classe.

## <a name="word-document-protection-in-the-designer"></a>Proteção de documentos do Word no designer
 Se você adicionar proteção a um documento ou modelo do Word enquanto ele estiver aberto no Visual Studio, não poderá iniciar a imposição da proteção no designer. O documento está no modo de design enquanto está aberto no Visual Studio e deve estar em modo de execução antes que você possa começar a impor a proteção.

 No entanto, se você criar um projeto que usa um documento do Word existente com proteção habilitada, o documento será protegido enquanto estiver aberto no designer. Não é possível editar as partes protegidas do documento, mas você ainda pode escrever código no editor de código para automatizar o documento. Você também não poderá compilar o projeto se a proteção estiver habilitada enquanto o documento estiver aberto no Visual Studio.

 Você pode desativar a proteção enquanto o documento está aberto no designer para que você possa editar o documento e criar o projeto. Não é possível desativar a proteção para a cópia no designer enquanto você está depurando; o documento que é aberto durante a depuração é uma cópia separada da aberta no designer (a cópia de saída é armazenada no diretório *\Bin* para Visual Basic e o diretório *\bin\Debug* para C#).

 Você pode habilitar a proteção na cópia do documento que é aberta no designer fechando o projeto no Visual Studio, abrindo a cópia do documento que está no diretório do projeto e ativando a proteção.

## <a name="enforce-word-document-protection-on-build"></a>Impor proteção de documentos do Word na compilação
 O Visual Studio começa a impor a proteção para documentos e modelos do Word durante o processo de compilação, para que a proteção seja habilitada quando o documento for aberto para depuração. O documento está protegido com uma senha vazia.

 A proteção é habilitada durante a compilação, de forma que, se <xref:Microsoft.Office.Tools.Word.Document.Startup> houver código no evento de documento que possa causar exceções ou alterar o comportamento do aplicativo, esse código poderá ser depurado corretamente. Se você habilitar a proteção depois que o documento for aberto, o código de inicialização não poderá ser depurado ou testado.

## <a name="setting-the-password"></a>Definindo a senha
 O Visual Studio habilita automaticamente a proteção, mas não fornece nenhuma senha por padrão. Se desejar que a proteção do documento tenha uma senha, você deverá adicioná-la antes de implantar sua solução. A adição de uma senha permite que os usuários autorizados removam a proteção do documento; sem uma senha, a proteção não pode ser facilmente removida. Para obter detalhes sobre como definir uma senha, consulte a ajuda no aplicativo específico do Office.

## <a name="see-also"></a>Consulte também
- [Como: Proteger documentos e partes de documentos programaticamente](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)
- [Exemplos e orientações de desenvolvimento do Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Visão geral do gerenciamento de direitos de informação e extensões de código gerenciado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Proteção por senha em documentos do Office](../vsto/password-protection-on-office-documents.md)
- [Como: Permitir que o código execute por trás de documentos com permissões restritas](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
