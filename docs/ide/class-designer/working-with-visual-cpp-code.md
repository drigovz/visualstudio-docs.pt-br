---
title: Trabalhando com código C++ (Designer de Classe)
description: Saiba como usar diagramas de classe para criar e Visualizar elementos de código C++, classes e outros tipos em um projeto.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- C++, Class Designer
- Class Designer, C++ support
- Class Designer, limitations
- Class Designer, tasks in C++
- C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 62993611ef7359095512f494767bbd3ea4cce5d9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946573"
---
# <a name="work-with-c-code-in-class-designer"></a>Trabalhar com código C++ no Designer de Classe

O **Designer de Classe** exibe uma superfície de design visual chamada de *diagrama de classe* que fornece uma representação visual dos elementos de código no projeto. É possível usar diagramas de classe para criar e visualizar classes e outros tipos em um projeto.

O **Designer de Classe** é compatível com os seguintes elementos de código C++:

- Classe (semelhante a uma forma de classe gerenciada, com exceção de que ela pode ter vários relacionamentos de herança)

- Classe anônima (exibe o nome gerado do Modo de Exibição de Classe para o tipo anônimo)

- Classe de modelo

- Estrutura

- Enumeração

- Macro (exibe a exibição pós-processada da macro)

- Typedef

> [!NOTE]
> Isso não é o mesmo que o diagrama de classe UML, que pode ser criado em um Projeto de Modelagem. Para obter mais informações, consulte [Diagramas de classe UML: Referência](../../modeling/what-s-new-for-design-in-visual-studio.md).

## <a name="troubleshoot-type-resolution-and-display-issues"></a>Solucionar problemas de exibição e resolução de tipo

### <a name="location-of-source-files"></a>Local dos arquivos de origem

O **Designer de Classe** não mantém um controle sobre a localização dos arquivos de origem. Portanto, se você modificar a estrutura do projeto ou mover os arquivos de origem no projeto, o **Designer de Classe** poderá perder o controle do tipo (principalmente do tipo de origem de um typedef, de classes base ou de tipos de associação). É possível receber um erro como **O Designer de Classe não pode exibir este tipo**. Se você fizer isso, arraste o código-fonte realocado ou modificado para o diagrama de classe, para exibi-lo novamente.

### <a name="update-and-performance-issues"></a>Problemas de atualização e de desempenho

Para projetos C++, pode levar de 30 a 60 segundos para que uma alteração no arquivo de origem apareça no diagrama de classe. Esse atraso também pode fazer com que o **Designer de Classe** gere o erro **Não foi encontrado nenhum tipo na seleção**. Se você receber um erro como esse, clique em **Cancelar** na mensagem de erro e espere até que o elemento de código seja exibido no **Modo de Exibição de Classe**. Depois de fazer isso, o **Designer de Classe** deverá exibir o tipo.

Se um diagrama de classe não for atualizado com as alterações feitas no código, talvez seja necessário fechar o diagrama e abri-lo novamente.

### <a name="type-resolution-issues"></a>Problemas de resolução de tipo

O **Designer de Classe** pode não conseguir resolver tipos pelos seguintes motivos:

- O tipo está em um projeto ou assembly que não é referenciado no projeto que contém o diagrama de classe. Para corrigir esse erro, adicione uma referência ao projeto ou ao assembly que contém o tipo. Para obter mais informações, consulte [Gerenciando referências em um projeto](../managing-references-in-a-project.md).

- O tipo não está no escopo correto e, portanto, o **Designer de Classe** não pode localizá-lo. Verifique se o código não tem uma declaração `using`, `imports` ou `#include` ausente. Além disso, verifique se você não moveu o tipo (ou um tipo relacionado) para fora do namespace em que ele estava originalmente localizado.

- O tipo não existe (ou foi comentado). Para corrigir esse erro, verifique se você não comentou nem excluiu o tipo.

- O tipo está localizado em uma biblioteca referenciada por uma diretiva #import. Uma possível solução alternativa é adicionar o código gerado (o arquivo .tlh) manualmente a uma diretiva #include no arquivo de cabeçalho.

- Verifique se o **Designer de Classe** é compatível com o tipo inserido. Consulte [Limitações de elementos de código C++](#limitations-for-c-code-elements).

O erro que você provavelmente encontrará para um problema de resolução de tipo **não foi possível encontrar o código para uma ou mais formas no diagrama de classe ' \<element> '**. Essa mensagem de erro não indica necessariamente que o código tem um erro. Ela indica apenas que o designer de classe não pôde exibir o código. Tente as seguintes medidas:

- Verifique se o tipo existe. Verifique se você não comentou nem excluiu o código-fonte acidentalmente.

- Tente resolver o tipo. O tipo pode estar em um projeto ou assembly que não é referenciado no projeto que contém o diagrama de classe. Para corrigir esse erro, adicione uma referência ao projeto ou ao assembly que contém o tipo. Para obter mais informações, consulte [Gerenciando referências em um projeto](../managing-references-in-a-project.md).

- Verifique se o tipo está no escopo correto para que o Designer de Classe possa localizá-lo. Verifique se o código não tem uma declaração `using`, `imports` ou `#include` ausente. Além disso, verifique se você não moveu o tipo (ou um tipo relacionado) para fora do namespace em que ele estava originalmente localizado.

### <a name="troubleshoot-other-error-messages"></a>Solucionar problemas de outras mensagens de erro

Você pode obter ajuda com a solução de erros e avisos nos fóruns públicos do Microsoft Developer Network (MSDN). Visite o [Fórum do Designer de Classe do Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsclassdesigner).

## <a name="limitations-for-c-code-elements"></a>Limitações para elementos de código C++

- Quando um projeto C++ é carregado, o **Designer de classe** funciona de maneira somente leitura. É possível alterar o diagrama de classe, mas não é possível salvar alterações do diagrama de classe de volta no código-fonte.

- O **Designer de Classe** é compatível com somente a semântica nativa do C++. Para projetos C++ que são compilados em código gerenciado, **Designer de classe** visualizarão apenas elementos de código que são tipos nativos. Portanto, é possível adicionar um diagrama de classe a um projeto, mas o **Designer de Classe** não permitirá a visualização de elementos nos quais a propriedade `IsManaged` esteja definida como `true` (ou seja, tipos de valor e tipos de referência).

- Para projetos C++, o **Designer de classe** lê apenas a definição do tipo. Por exemplo, suponha que você defina um tipo em um arquivo de cabeçalho (.h) e defina seus membros em um arquivo de implementação (.cpp). Se você invocar “Exibir Diagrama de Classe” no arquivo de implementação (.cpp), o **Designer de Classe** não exibirá nada. Como outro exemplo, se você invocar “Exibir Diagrama de Classe” em um arquivo .cpp que use uma instrução `#include` para incluir outros arquivos, mas que não contenha nenhuma definição de classe real, o **Designer de Classe** não exibirá nada novamente.

- Arquivos IDL (.idl), que definem interfaces COM e bibliotecas de tipo, não exibem diagramas, a menos que sejam compilados para o código C++ nativo.

- O **Designer de Classe** não é compatível com funções e variáveis globais.

- **Designer de Classe** não é compatível com uniões. Esse é um tipo especial de classe no qual a memória alocada é apenas a quantidade necessária para o maior membro de dados da união.

- O **Designer de Classe** não exibe tipos de dados básicos como `int` e `char`.

- O **Designer de Classe** não exibe tipos que são definidos fora do projeto atual se o projeto não tem referências corretas para esses tipos.

- O **Designer de Classe** pode exibir tipos aninhados, mas não as relações entre um tipo aninhado e outros tipos.

- O **Designer de Classe** não pode exibir tipos que são nulos ou derivados de um tipo nulo.

## <a name="see-also"></a>Consulte também

- [Projetando e exibindo classes e tipos](designing-and-viewing-classes-and-types.md)
- [Informações adicionais sobre erros do Designer de Classe](additional-information-about-errors.md)
- [Classes C++ no Designer de Classe](visual-cpp-classes.md)
- [Estruturas do C++ no Designer de Classe](visual-cpp-structures.md)
- [Enumerações C++ no Designer de Classe](visual-cpp-enumerations.md)
- [TYPEDEFs C++ no Designer de Classe](visual-cpp-typedefs.md)
