---
title: 'Como: Depurar um executável que não faz parte de uma solução do Visual Studio | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e33233fd313cd6a73013ce55333a860663ddb601
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704519"
---
# <a name="how-to-debug-an-executable-not-part-of-a-visual-studio-solution"></a>Como depurar um executável que não faça parte de uma solução do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Às vezes, convém depurar um executável que não é parte de um projeto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Pode ser um executável criado fora do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou um executável que você recebeu de outra pessoa.  
  
 A resposta usual para esse problema é iniciar a parte externa executável do Visual Studio e anexá-la a ele usando o depurador [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para obter mais informações, consulte[anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Anexar a um aplicativo requer algumas etapas manuais, por isso demora alguns segundos. Este pequeno atraso significa que a anexação não ajudará se você estiver tentando depurar um problema que ocorre durante a inicialização. Além disso, se você estiver depurando um programa que não aguarda a entrada do usuário, e fecha rapidamente, você poderá não ter tempo para anexar a ele. Se você tiver o [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] instalado, poderá criar um projeto EXE para tal programa.  
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Para criar um projeto EXE para um executável existente  
  
1. No menu **arquivo** , clique em **abrir** e selecione **projeto**.  
  
2. Na caixa de diálogo **Abrir projeto** , clique na lista suspensa ao lado da caixa **nome do arquivo** e selecione **todos os arquivos de projeto**.  
  
3. Localize o executável e clique em **OK**.  
  
     Isso cria uma solução temporária que contém o executável.  
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Para importar um executável em uma solução do Visual Studio  
  
1. No menu **arquivo** , aponte para **Adicionar projeto**e clique em **projeto existente**.  
  
2. Na caixa de diálogo **Adicionar projeto existente** , clique na lista suspensa ao lado da caixa **nome do arquivo** e selecione **todos os arquivos de projeto**.  
  
3. Localize e selecione o executável.  
  
4. Clique em **OK**.  
  
5. Inicie o executável escolhendo um comando de execução, como **Iniciar**, no menu **depurar** .  
  
    > [!NOTE]
    > Nem todas as linguagens de programação oferecem suporte a projetos EXE. Instale o [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] se precisar usar esse recurso.  
  
     Quando você estiver depurando um executável sem código-fonte, os recursos de depuração disponíveis serão limitados, independente de você anexar a um executável em execução ou adicionar o executável a uma solução do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Se o arquivo executável for compilado sem informações de depuração em um formato compatível, os recursos disponíveis serão mais limitados. Se você tiver o código-fonte, a melhor abordagem será importar o código-fonte para o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e criar uma compilação de depuração do executável no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Consulte Também  
 [Configurações e preparação do depurador](../debugger/debugger-settings-and-preparation.md)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Arquivos DBG](https://msdn.microsoft.com/91e449e9-8b65-4123-960f-2107cd1f1cfd)
