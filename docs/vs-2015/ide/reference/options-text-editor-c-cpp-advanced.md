---
title: Opções, Editor de Texto, C/C++, Avançado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C\C++.Advanced
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Advanced
- VS.ToolsOptionsPages.Text_Editor.C/C++.Advanced
helpviewer_keywords:
- Text Editor Options dialog box, advanced
ms.assetid: 67c82ae5-fddd-49df-baec-8e7498b156f3
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 236135cd4b4f813471ece7a0eeb1b221c7242df9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662360"
---
# <a name="options-text-editor-cc-advanced"></a>Opções, Editor de Texto, C/C++, Avançado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ao alterar essas opções, você pode alterar o comportamento relacionado ao IntelliSense e ao banco de dados de navegação quando estiver programando em C ou C++.

 Para acessar essa página, na caixa de diálogo **Opções**, no painel esquerdo, expanda **Editor de Texto**, expanda **C/C++** e escolha **Avançado**.

> [!NOTE]
> Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="browsingnavigation"></a>Navegação
 Você nunca deve escolher essas opções, exceto no caso raro em que uma solução é tão grande que a atividade de banco de dados consome uma quantidade inaceitável de recursos do sistema.

 **Desabilitar banco de dados** Todo o uso do banco de dados de navegação de código (SDF), todas as outras opções de navegação/navegações e todos os recursos do IntelliSense, exceto para #include preenchimento automático, estão desabilitados.

 **Desabilitar atualizações de banco de dados** O banco de dados será aberto como somente leitura e nenhuma atualização será executada à medida que os arquivos forem editados. A maioria dos recursos ainda funcionará. No entanto, como são feitas edições, os dados ficarão obsoletos e você obterá resultados incorretos.

 **Desabilitar atualizações automáticas do banco de dados** O banco de dados de navegação de código não será atualizado automaticamente quando os arquivos de origem forem modificados. No entanto, se você abrir o **Gerenciador de Soluções**, abra o menu de atalho do projeto e escolha **Examinar Novamente a Solução**, todos os arquivos desatualizados serão verificados e o banco de dados será atualizado.

 **Desabilitar arquivos implícitos** O banco de dados de navegação de código não coleta os arquivos que não são especificados em um projeto. Um projeto contém arquivos de origem e arquivos de cabeçalho que são especificados explicitamente. Os arquivos implícitos são incluídos por arquivos explícitos (por exemplo, afxwin.h, windows.h e atlbase.h). Normalmente, o sistema localiza esses arquivos e também os indexa para vários recursos de navegação (incluindo Navegar Até). Se você escolher essa opção, esses arquivos não serão indexados e alguns recursos não estarão disponíveis para eles. Se você escolher essa opção, "Desabilitar Limpeza Implícita" e "Desabilitar Pastas de Dependências Externas" também são implicitamente escolhidas.

 **Desabilitar limpeza implícita** O banco de dados de navegação de código não limpa arquivos implícitos que não são mais referenciados. Essa opção impede que arquivos implícitos sejam removidos do banco de dados quando não são mais usados. Por exemplo, se você adicionar um a diretiva `#include` que referencia mapi.h a um dos seus arquivos de origem, mapi.h será encontrado e indexado. Se você, em seguida, remover o #include e o arquivo não for referenciado em outro lugar, as informações sobre ele eventualmente serão removidas a menos que você escolha essa opção. (Consulte a opção **examinar novamente o intervalo de solução** .) Essa opção é ignorada quando você examina a solução de forma explícita.

 **Desabilitar pastas de dependências externas** A pasta de dependências externas para cada projeto não é criada ou atualizada. No **Gerenciador de Soluções**, cada projeto contém uma pasta de Dependências Externas, que contém todos os arquivos implícitos daquele projeto. Se você escolher essa opção, essa pasta não desaparece.

 **Recriar banco de dados** Recrie o banco de dados de navegação de código de nada na próxima vez que a solução for carregada. Se você escolher essa opção, o arquivo de banco de dados SDF será excluído na próxima vez em que você carregar a solução, fazendo assim com que o banco de dados seja recriado e todos os arquivos sejam indexados.

 **Examinar intervalo da solução novamente** Um trabalho ' examinar novamente solução agora ' está agendado para o intervalo especificado. Você deve especificar entre 0 e 5000 minutos. O valor padrão é 60 minutos. Enquanto a solução é verificada novamente, os carimbos de data/hora do arquivo são verificados para determinar se o arquivo foi alterado fora do IDE. (As alterações feitas no IDE são automaticamente rastreadas e os arquivos são atualizados.) Os arquivos incluídos implicitamente são verificados para determinar se todos eles ainda são referenciados.

## <a name="diagnostic-logging"></a>Diagnostic Logging
 Essas opções são fornecidas no caso de a Microsoft solicitar a coleta de informações avançadas para diagnosticar um problema. As informações de log não são úteis para os usuários e é recomendável deixá-las desabilitadas.

 **Habilitar registro em log** Habilita o log de diagnóstico para a janela de saída.

 **Nível de log** Defina o detalhamento do log, de 0 a 5.

 **Filtro de log** Filtros exibidos tipos de evento usando uma bitmask.

 Defina usando uma soma de qualquer uma das seguintes opções:

- 0 – Nenhum

- 1 – Geral

- 2 – Ocioso

- 4 – WorkItem

- 8 – IntelliSense

- 16 – ACPerf

- 32 – ClassView

## <a name="fallback-location"></a>Localização de Fallback
 A localização de fallback é onde os arquivos de suporte SDF e IntelliSense (por exemplo, iPCH) são colocados quando a localização principal (mesmo diretório que a solução) não é usado. Essa situação pode ocorrer se o usuário não tem as permissões para gravar no diretório da solução ou o diretório da solução está em um dispositivo lento. A localização de fallback padrão é no diretório temporário do usuário.

 **Sempre usar local de fallback** Indica que o banco de dados de navegação de código e os arquivos do IntelliSense sempre devem ser armazenados em uma pasta que você especifica como seu "local de fallback", não ao lado do arquivo. sln. O IDE nunca tentará colocar os arquivos SDF ou iPCH próximos ao diretório da solução e sempre tentará usar a localização de fallback.

 Não **avisar se o local de fallback for usado** Você não será informado ou solicitado se um ' local de fallback ' for usado. Normalmente, o IDE informará se precisar usar a localização de fallback. Esta opção desativa esse aviso.

 **Local de fallback** Esse valor é usado como um local secundário para armazenar o banco de dados de navegação de código ou arquivos IntelliSense. Por padrão, o diretório temporário é o local de fallback. O IDE criará um subdiretório no caminho especificado (ou no diretório temporário) que inclui o nome da solução junto com um hash do caminho completo para a solução, o que evita problemas com nomes de solução serem idênticos.

## <a name="intellisense"></a>IntelliSense
 **Informações rápidas automáticas** Habilita dicas de ferramenta QuickInfo quando você move o ponteiro do mouse sobre o texto.

 **Desabilitar o IntelliSense** Desabilita todos os recursos do IntelliSense. O IDE não cria processos VCPkgSrv.exe para atender a solicitações do IntelliSense e nenhum recurso do IntelliSense funcionará (QuickInfo, Lista de Membros, Preenchimento Automático, Ajuda de Parâmetro). A colorização semântica e o realce de referência também são desabilitados. Essa opção não desabilita recursos de navegação que dependem exclusivamente do banco de dados (incluindo a Barra de Navegação, ClassView e janela Propriedade).

 **Desabilitar a atualização automática** A atualização do IntelliSense é atrasada até que uma solicitação real do IntelliSense seja feita. Esse atraso pode resultar em um tempo de execução maior da primeira operação do IntelliSense em um arquivo, mas pode ser útil definir esta opção em computadores muito lentos ou com recursos limitados. Se você escolher essa opção, também escolherá implicitamente as opções “Desabilitar Relatório de Erros” e “Desabilitar Rabiscos”.

 **Desabilitar relatório de erros** Desabilita a emissão de relatórios de erros do IntelliSense por meio de rabiscos e da janela de Lista de Erros. Também desabilita a análise em segundo plano que está associada ao relatório de erros. Se você escolher essa opção, também escolherá implicitamente a opção “Desabilitar Rabiscos”.

 **Desabilitar rabiscos** Desabilita os rabiscos de erro do IntelliSense. Os “rabiscos” vermelhos não aparecem na janela do editor, mas o erro ainda aparecerá na janela Lista de Erros.

 **Desabilitar #include preenchimento automático** Desabilita a conclusão automática de `#include` instruções.

 **Usar barra em #include preenchimento automático** Dispara a conclusão automática de `#include` instruções quando "/" é usado. O delimitador padrão é a barra invertida “ \”. O compilador pode aceitar qualquer um, então use esta opção para especificar o que sua base de código usa.

 **Máximo de unidades de conversão em cache** O número máximo de unidades de tradução que serão mantidas ativas a qualquer momento para solicitações do IntelliSense. Você deve especificar um valor entre 2 e 15. Esse número está diretamente relacionado ao número máximo de processos de VCPkgSrv.exe que serão executados (para uma determinada instância do Visual Studio). O valor padrão é 2, mas se você tiver memória disponível, poderá aumentar esse valor e possivelmente alcançar um desempenho ligeiramente melhor no IntelliSense.

 Para obter mais informações sobre as unidades de translação, consulte [Fases de translação](https://msdn.microsoft.com/library/a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db).

 **Desabilitar a lista agressiva de membros** A lista de membros não aparece enquanto você digita o nome de um tipo ou variável. A lista é exibida somente depois que você digita um dos caracteres de confirmação, conforme definido na opção **Caracteres de Confirmação de Lista de Membros**.

 **Desabilitar palavras-chave da lista de membros** Palavras-chave de idioma como `void` , `class` , `switch` não aparecem em sugestões de lista de membros.

 **Desabilitar trechos de código de lista de membros** Os trechos de código não aparecem nas sugestões da lista de membros.

 **Desabilitar colorização semântica** Desativa toda a colorização de código, exceto palavras-chave de idioma, cadeias de caracteres e comentários.

 **Confirmação da lista de membros inteligentes** Adiciona uma linha quando você escolhe a tecla Enter no final de uma palavra totalmente digitada.

 **Modo de filtro da lista de membros** Define o tipo de algoritmo de correspondência. **Difuso** localiza as correspondências mais possíveis porque usa um algoritmo semelhante a um verificador ortográfico para localizar correspondências semelhantes, mas não idênticas. **Filtragem inteligente** corresponde subcadeias de caracteres, mesmo que não estejam no início de uma palavra. **Prefixo** corresponde apenas em subcadeias de caracteres idênticas que começam no início da palavra.

 **Caracteres de confirmação da lista de membros** Especifica os caracteres que fazem com que a sugestão da lista de membros realçada no momento seja confirmada. Você pode adicionar ou remover caracteres desta lista.

## <a name="references"></a>Referências
 **Desabilitar resolução** Por motivos de desempenho, "localizar todas as referências" exibe os resultados brutos da pesquisa textual por padrão em vez de usar o IntelliSense para verificar cada candidato. Você pode desmarcar essa caixa de seleção para obter resultados mais precisos em todas as operações de pesquisa. Para filtrar por pesquisa, abra o menu de atalho para a lista de resultados e, em seguida, escolha "Resolver Resultados".

 **Ocultar não confirmados** Ocultar itens não confirmados nos resultados de ' Localizar todas as referências '. Se você remover definição da opção "Desabilitar Resolução", poderá usar essa opção para ocultar itens não confirmados nos resultados.

 **Desabilitar Realce de Referência**

## <a name="see-also"></a>Consulte Também
 [Configurando opções de editor específicas de idioma](../../ide/reference/setting-language-specific-editor-options.md)
