---
title: Consulte as dependências entre C++ arquivos de origem e de cabeçalho
ms.date: 05/16/2018
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbba97f47c3ac0686bad15c3a1882e1e9bd85057
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654189"
---
# <a name="code-maps-for-c-projects"></a>Mapas de código C++ para projetos

Se você quiser criar mapas mais completos para C++ projetos, defina a opção de compilador de informações de procura ( **/fr**) nesses projetos. Do contrário, uma mensagem é exibida e solicita a definição dessa opção. Se você selecionar **OK**, isso definirá a opção apenas para o mapa atual. Você pode optar por ocultar a mensagem para todos os mapas posteriores.

Quando você abre uma solução que contém projetos do Visual C++, pode demorar algum tempo para atualizar o banco de dados do IntelliSense. Durante esse tempo, talvez você não consiga criar mapas de código para arquivos de cabeçalho ( *. h* ou `#include`) até que o banco de dados do IntelliSense termine a atualização. É possível monitorar o andamento da atualização na barra de status do Visual Studio.

- Para ver as dependências entre todos os arquivos de origem e arquivos de cabeçalho em sua solução, selecione **arquitetura**  > **gerar grafo de arquivos de inclusão**.

   ![Grafo de dependência para código nativo](../modeling/media/dependencygraphgeneral_nativecode.png)

- Para ver as dependências entre os arquivos abertos atualmente, os arquivos de origem relacionados e os arquivos de cabeçalho, abra o arquivo de origem ou o arquivo de cabeçalho. Abra o menu de atalho do arquivo em qualquer lugar dentro do arquivo. Escolha **gerar grafo de arquivos de inclusão**.

   ![Grafo de dependência de primeiro nível para arquivo. h](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>Solucionar problemas de mapas de C++ código para C e Code

Esses itens não são suportados para os códigos C e C++:

- Os tipos base não aparecem em mapas que incluem a hierarquia pai.

- A **maioria dos** itens de menu não estão disponíveis C++ para C e code.

Esses problemas podem ocorrer quando você cria mapas de código para C C++ e código:

|**Lo**|**Causa possível**|**Resolução**|
|-|-|-|
|Falha ao gerar o mapa de códigos.|Nenhum projeto na solução foi compilado com êxito.|Corrija os erros de compilação que ocorreram e, em seguida, gere o mapa novamente.|
|O Visual Studio deixa de responder quando você tenta gerar um mapa de código no menu **arquitetura** .|O arquivo de banco de dados do programa (.pdb) pode estar corrompido.<br /><br /> Um arquivo .pdb armazena informações de depuração, como o tipo, o método e as informações do arquivo de origem.|Recompile a solução e, em seguida, tente novamente.|
|Determinadas configurações do banco de dados de navegação do IntelliSense estão desabilitadas.|Determinadas configurações do IntelliSense podem ser desabilitadas na caixa de diálogo **Opções** do Visual Studio.|Ative as configurações para habilitá-las.<br /><br /> Consulte [Opções, editor de texto, CC++/, avançado](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|A mensagem **métodos desconhecidos** aparece em um nó de método.<br /><br /> Esse problema ocorre porque o nome do método não pode ser resolvido.|O arquivo binário não pode ter uma tabela de realocação de base.|Ative a opção **/Fixed:** no do vinculador.|
||Talvez o arquivo de banco de dados do programa (.pdb) não tenha sido compilado.<br /><br /> Um arquivo .pdb armazena informações de depuração, como o tipo, o método e as informações do arquivo de origem.|Ative a opção **/debug** no vinculador.|
||Não é possível abrir ou encontrar o arquivo .pdb em locais esperados.|Verifique se o arquivo .pdb existe nos locais esperados.|
||As informações de depuração foram removidas do arquivo .pdb.|Se a opção **/PDBSTRIPPED** foi usada no vinculador, inclua o arquivo. pdb completo.|
||O chamador não é uma função, e é uma conversão no arquivo binário ou um ponteiro na seção de dados.|Quando o chamador for uma conversão, tente usar `_declspec(dllimport)` para evitá-la.|

## <a name="see-also"></a>Consulte também

- [Mapear dependências com mapas de código](../modeling/map-dependencies-across-your-solutions.md)