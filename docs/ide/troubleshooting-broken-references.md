---
title: Solução de problemas de referências desfeitas
description: Saiba como solucionar problemas de referências quebradas que podem ser causadas por algo diferente da incapacidade do seu aplicativo de encontrar o componente referenciado.
ms.custom: SEO-VS-2020
ms.date: 03/21/2017
ms.topic: troubleshooting
helpviewer_keywords:
- C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 75e4d04641d593d8ced0c696cdca1efffd95e48d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971499"
---
# <a name="troubleshoot-broken-references"></a>Solução de problemas de referências desfeitas

Se o aplicativo tentar usar uma referência desfeita, um erro de exceção será gerado. A incapacidade de localizar o componente referenciado é o gatilho primário do erro, mas existem várias situações em que uma referência pode ser considerada desfeita. Essas instâncias são mostradas na seguinte lista:

- O caminho de referência do projeto está incorreto ou incompleto.

- O arquivo que está sendo referenciado foi excluído.

- O arquivo que está sendo referenciado foi renomeado.

- A conexão de rede ou a autenticação falhou.

- A referência indica um componente COM que não está instalado no computador.

Veja a seguir as soluções para esses problemas.

> [!NOTE]
> Os arquivos em assemblies são referenciados com caminhos absolutos no arquivo de projeto. Portanto, é possível que os usuários que trabalham em um ambiente com vários desenvolvedores tenham um assembly referenciado ausente no ambiente local. Para evitar esses erros, nesses casos, é melhor adicionar referências projeto a projeto. Para obter mais informações, consulte [programação com assemblies](/dotnet/framework/app-domains/programming-with-assemblies).

## <a name="reference-path-is-incorrect"></a>O caminho de referência está incorreto

Se os projetos forem compartilhados em computadores diferentes, algumas referências poderão não ser encontradas quando um componente estiver localizado em um diretório diferente de cada computador. As referências são armazenadas sob o nome do arquivo de componente (por exemplo, *myComponent*). Quando uma referência é adicionada a um projeto, o local da pasta do arquivo de componente (por exemplo, *C:\MyComponents*) é acrescentado à propriedade de projeto **ReferencePath** .

Quando o projeto é aberto, ele tenta localizar esses arquivos de componentes referenciados procurando nos diretórios no caminho de referência. Se o projeto for aberto em um computador que armazena o componente em um diretório diferente, como *D:\MyComponents*, a referência não poderá ser encontrada e um erro aparecerá na **lista de tarefas**.

Para corrigir esse problema, você pode excluir a referência quebrada e substituí-la usando a caixa de diálogo **Adicionar referência** . Outra solução é usar o item **Caminho de Referência** nas páginas de propriedades do projeto e modificar as pastas na lista para que elas apontem para os locais corretos. A propriedade **Caminho de Referência** é persistida para cada usuário em cada computador. Portanto, a modificação do caminho de referência não afeta outros usuários do projeto.

> [!TIP]
> Referências projeto a projeto não apresentam esses problemas. Por esse motivo, se possível, use-as, em vez de referências de arquivo.

### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Para corrigir uma referência de projeto desfeita corrigindo o caminho de referência

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó do projeto e clique em **Propriedades**.

   O **Designer de projeto** é exibido.

1. Se você estiver usando o Visual Basic, selecione a página **Referências** e clique no botão **Caminhos de Referência**. Na caixa de diálogo **Caminhos de Referência**, digite o caminho da pasta que contém o item que você deseja referenciar no campo **Pasta** e, em seguida, clique no botão **Adicionar Pasta**.

    Se estiver usando o C#, selecione a página **Caminhos de Referência**. No campo **Pasta**, digite o caminho da pasta que contém o item que você deseja referenciar e, em seguida, clique no botão **Adicionar Pasta**.

## <a name="referenced-file-has-been-deleted"></a>O arquivo referenciado foi excluído

É possível que o arquivo que está sendo referenciado tenha sido excluído e não exista mais na unidade.

### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Para corrigir uma referência de projeto desfeita de um arquivo que não existe mais na unidade

- Exclua a referência.

- Se a referência existir em outro local do computador, leia-a nesse local.

## <a name="referenced-file-has-been-renamed"></a>O arquivo referenciado foi renomeado

É possível que o arquivo que está sendo referenciado tenha sido renomeado.

### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Para corrigir uma referência desfeita de um arquivo que foi renomeado

- Exclua a referência e, em seguida, adicione uma referência ao arquivo renomeado.

- Se a referência existir em outro local do computador, será necessário lê-la nesse local.

## <a name="network-connection-or-authentication-has-failed"></a>A conexão de rede ou a autenticação falhou

Pode haver várias causas possíveis para arquivos inacessíveis: uma conexão de rede ou uma autenticação com falha, por exemplo. Cada causa pode ter meios exclusivos de recuperação; por exemplo, você poderá precisar contatar o administrador local para acessar os recursos necessários. No entanto, a exclusão da referência e a correção do código que a usou é sempre uma opção.

## <a name="com-component-is-not-installed-on-computer"></a>O componente COM não está instalado no computador

Se um usuário tiver adicionado uma referência a um componente COM e um segundo usuário tentar executar o código em um computador que não tem esse componente instalado, o segundo usuário receberá um erro informando de que a referência está desfeita. Instalar o componente no segundo computador corrigirá o erro. Para obter mais informações sobre como usar referências a componentes COM em seus projetos, consulte [interoperabilidade com em aplicativos .NET Framework](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications).

## <a name="see-also"></a>Confira também

- [Página Referências, Designer de Projeto (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)
