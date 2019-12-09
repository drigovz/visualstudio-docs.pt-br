---
title: 'Como: Alterar o diretório de saída do build'
ms.date: 05/15/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 493de227174b60b4834c2732ddbf16a5586fa49e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238180"
---
# <a name="how-to-change-the-build-output-directory"></a>Como: Alterar o diretório de saída do build

Você pode especificar o local de saída gerado pelo seu projeto por configuração (para depuração, versão ou ambas).

## <a name="change-the-build-output-directory"></a>Alterar o diretório de saída do build

1. Para abrir as páginas de propriedades do projeto, clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecione **Propriedades**.

2. Selecione a guia apropriada com base no tipo de projeto:

   - Para C#, selecione a guia **Compilar**.
   - Para o Visual Basic, selecione a guia **Compilar**.
   - Para C++ ou JavaScript, selecione a guia **Geral**.

3. Na lista suspensa de configuração na parte superior, escolha a configuração cujo local do arquivo de saída você deseja alterar (**Depuração**, **Versão** ou **Todas as Configurações**).

4. Localize a entrada de caminho de saída na página&mdash;ele é diferente, dependendo de seu tipo de projeto:

   - **Caminho de saída** para projetos C# e JavaScript
   - **Caminho de saída de build** para projetos Visual Basic
   - **Diretório de saída** para projetos Visual C++

   Digite o caminho para o qual gerar a saída (absoluto ou relativo para o diretório raiz do projeto), ou escolha **Procurar** para, em vez disso, navegar até essa pasta.

   ![Propriedade de caminho de saída para um projeto C# do Visual Studio](media/output-path.png)
   
   > [!NOTE]
   > Alguns projetos incluirão, por padrão, a estrutura e o tempo de execução no caminho de compilação. Para alterar isso, clique com o botão direito do mouse no nó do projeto em **Gerenciador de soluções**, selecione **Editar arquivo de projeto**e adicione o seguinte:
   > ```xml
   > <PropertyGroup>
   >   <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
   >   <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
   > </PropertyGroup>
   > ```

> [!TIP]
> Se a saída não está sendo gerada para o local que especificou, verifique se você está compilando a configuração correspondente (por exemplo, **Depuração** ou **Versão**), selecionando-a na barra de menus do Visual Studio.
>
> ![Seletor de configuração de build do Visual Studio de 2019](media/build-configuration-chooser.png)

## <a name="see-also"></a>Consulte também

- [Página de build, Designer de Projeto (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Página de propriedades gerais (projeto)](/cpp/build/reference/general-property-page-project)
- [Compilação e build](../ide/compiling-and-building-in-visual-studio.md)
