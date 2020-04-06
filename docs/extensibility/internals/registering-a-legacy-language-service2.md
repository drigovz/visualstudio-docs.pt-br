---
title: Registrando um serviço de idioma legado2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d9d13f301f6c04c0f7b14cc8c685f08b072ef84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705882"
---
# <a name="registering-a-legacy-language-service"></a>Registrar um serviço de linguagem herdado
As seções a seguir fornecem listas de entradas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de registro para as várias opções de serviço de idioma disponíveis em .

 Na lista a seguir de entradas de registro, *VS Reg* Root\\é igual a HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio*X.Y*, onde *X.Y* é o número da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] versão.

## <a name="registry-entries-for-language-service-options"></a>Inscrições de registro para opções de serviço de idioma
 A *tecla VS Reg*Root\\\Languages\Languageservices's*Language Name* pode conter os seguintes valores.

|Nome|Type|Intervalo|Descrição|
|----------|----------|-----------|-----------------|
|(Padrão)|REG_SZ|*\<>GUID*|GUID do serviço de idiomas.|
|LangResID|REG_DWORD|0x0-0xffff|Identificador de recurso de string (ResID) para o nome de texto localizado do idioma.|
|Pacote|REG_SZ|*\<>GUID*|GUID do VSPackage.|
|ShowComplet|REG_DWORD|0-1|Especifica se as opções **de conclusão de declaração** na caixa de diálogo **Opções** estão habilitadas.|
|ShowSmartIndent|REG_DWORD|0-1|Especifica se a opção de selecionar **recuo Inteligente** na caixa de diálogo **Opções** está ativada.|
|RequestStockColors|REG_DWORD|0-1|Especifica se as cores personalizadas ou padrão são usadas para colorir palavras-chave.|
|ShowHotURLs|REG_DWORD|0-1|Especifica se o usuário pode clicar em URLs.|
|Padrão para URLs não quentes|REG_DWORD|0-1|Especifica a configuração inicial para a opção **Ativar navegação URL com um clique único** na caixa de diálogo **Opções.**|
|Padrãopara inserirespaços|REG_DWORD|0-1|Especifica se o serviço de idioma tem "inserir espaços" como opção de guia padrão.|
|ShowDropdownBarOption|REG_DWORD|0-1|Ativa ou desativa a opção **Barra de navegação** na caixa de diálogo **Opções** que mostra ou oculta a **barra de navegação**.|
|Somente janela de código único|REG_DWORD|0-1|Ativa ou desativa a escolha **da nova janela** no menu **Janela** para um serviço de idioma.|
|HabilitarAdvancedMembersOption|REG_DWORD|0-1|Ativa ou desativa uma configuração de caixa de diálogo **Opções** para **Ocultar Membros Avançados**.|
|CF_HTML de suporte|REG_DWORD|0-1|Especifica se o editor permite copiar e colar dados HTML.|
|EnablelineNumbersOption|REG_DWORD|0-1|Especifica se as opções **de números de linha** na caixa de diálogo **Opções** estão habilitadas para um serviço de idioma.|
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Especifica se membros avançados, como campos privados, estão escondidos em listas de conclusão.|
|ShowbraceComplet|REG_DWORD|0-1|Especifica se a opção **de conclusão do Brace** na caixa de diálogo **Opções** está ativada.|

### <a name="example"></a>Exemplo

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
        LangResID             = reg_dword:0x00000000
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}
        ShowCompletion        = reg_dword:0x00000001
        ShowSmartIndent       = reg_dword:0x00000001
        ShowDropdownBarOption = reg_dword:0x00000001
```

## <a name="registry-entries-for-debugger-languages-options"></a>Entradas de registro para opções de idiomas de depurador
 A tecla *VS Reg*Root\\\Languages\Language Services\\*Name*\Debugger Languages*GUID*\ pode incluir os seguintes valores.

|Nome|Type|Intervalo|Descrição|
|----------|----------|-----------|-----------------|
|(Padrão)|REG_SZ|text|O valor padrão pode ser usado para documentar o nome do idioma. O nome desta chave é um GUID de um avaliador de expressão que tem uma entrada correspondente no * \<VS Reg Root>* \AD7Metrics\Expression Evaluator.|

### <a name="example"></a>Exemplo

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        Debugger Languages\
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\
            (Default) = reg_sz:C++
```

## <a name="registry-entries-for-editor-tools-options"></a>Inscrições de registro para opções de ferramentas de editor
 Você pode adicionar chaves de registro na chave EditorToolsOptions para páginas de propriedade e nódes de propriedade. Essas chaves e seus valores identificam páginas de propriedade na caixa de diálogo **Opções** (no menu **Ferramentas)** usadas para configurar o serviço de idiomas. No exemplo a seguir, Nome da *página* é o nome de uma página de propriedade e *Nome do Nó* é o nome de um nó na árvore na caixa de diálogo **Opções.** A entrada da página e a entrada do nó devem ser especificadas separadamente.

|Nome|Type|Intervalo|Descrição|
|----------|----------|-----------|-----------------|
|(Padrão)|REG_SZ|Resid|O nome de exibição localizado desta página de opção. O nome pode ser texto`nnn`literal, ou # , onde `nnn` está um ID de recurso de seqüência no DLL do satélite do VSPackage especificado.|
|Pacote|REG_SZ|*Guid*|O GUID do VSPackage que implementa esta página de opções.|
|Página|REG_SZ|*Guid*|O GUID da página de propriedade para solicitar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> do VSPackage chamando o método. Se esta entrada de registro não estiver presente, a chave de registro descreverá um nó, não uma página.|

### <a name="example"></a>Exemplo

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      CSharp\
        EditorToolsOptions\
          Formatting\
            (Default) = reg_sz:#242
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
            General\
              (Default) = reg_sz:#255
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}
            Indentation\
              (Default) = reg_sz:#250
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}
            Newlines\
              (Default) = reg_sz:#253
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}
```

## <a name="registry-entries-for-file-name-extension-options"></a>Entradas de registro para opções de extensão de nome de arquivo
 A entrada para a extensão do arquivo deve incluir o período principal, por exemplo ".myext".

|Nome|Type|Intervalo|Descrição|
|----------|----------|-----------|-----------------|
|(Padrão)|REG_SZ|*Guid*|Guia de serviço para o serviço de idioma padrão para este tipo de extensão de nome de arquivo.|

### <a name="example"></a>Exemplo

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Entradas de registro para opções de editor
 A chave *VS Reg Root*\Editors pode conter os seguintes valores:

|Nome|Type|Intervalo|Descrição|
|----------|----------|-----------|-----------------|
|(Padrão)|REG_SZ|""|não utilizado; você pode colocar seu nome aqui para documentação.|
|DefaultToolboxTab|REG_SZ|""|Nome da guia caixa de ferramentas para tornar padrão quando o editor estiver ativo.|
|DisplayName|REG_SZ|Resid|Nome a ser exibido na **caixa de diálogo Abrir com** a caixa de diálogo. O nome é o ID de recurso de string ou um nome no formato padrão.|
|ExcluaDefTextEditor|REG_DWORD|0-1|Usado para o **comando Abrir com** menu. Se você não quiser listar o editor de texto padrão na lista de editores disponíveis para um tipo de arquivo específico, defina esse valor como 1.|
|LinkedEditorGUID|REG_SZ|*\<>GUID*|Usado para qualquer serviço de idioma que possa abrir um arquivo com suporte a páginas de código. Por exemplo, quando você abre um arquivo .txt usando o comando **Abrir Com,** são fornecidas opções para usar o editor de código-fonte com e sem codificação.<br /><br /> O GUID especificado no nome da subchave é para a fábrica do editor de páginas de código; o GUID vinculado especificado nesta entrada de registro específica é para a fábrica de editores regulares. O objetivo desta entrada é que se o IDE não abrir um arquivo usando o editor padrão, o IDE tentará usar o próximo editor da lista. Este próximo editor não deve ser a fábrica do editor de páginas de código porque esta fábrica de editores é basicamente a mesma que a fábrica de editores que falhou.|
|Pacote|REG_SZ|*\<>GUID*|VSPackage GUID para o nome de exibição é ResID.|

### <a name="example"></a>Exemplo

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      (Default)            = reg_sz:Html Editor with Encoding
      DefaultToolboxTab    = reg_sz:HTML
      DisplayName          = reg_sz:#20101
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}
```

## <a name="registry-entries-for-logical-view-options"></a>Inscrições de registro para opções de exibição lógica
 A *TEC Reg*Root\\\Editors*Editor GUI>* \LogicalViews key pode conter os seguintes valores.

|Nome|Type|Intervalo|Descrição|
|----------|----------|-----------|-----------------|
|(Padrão)|REG_SZ||Não utilizado.|
|*\<>GUID*|REG_SZ|""|Chave para as visões lógicas suportadas. Você pode ter quantos destes precisar. O nome da entrada de registro é o que é importante, não o valor, que é sempre uma seqüência vazia.|

### <a name="example"></a>Exemplo

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      LogicalViews\
       (Default) = reg_sz:
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
```

## <a name="registry-entries-for-editor-extension-options"></a>Inscrições de registro para opções de extensão do editor
 A tecla VS\\Reg *Root*\Editors*GUID*\Extensions pode conter os seguintes valores. A extensão do nome do arquivo não inclui o período principal.

|Nome|Type|Intervalo|Descrição|
|----------|----------|-----------|-----------------|
|(Padrão)|REG_SZ||Não utilizado.|
|*\<ext>*|REG_DWORD|0-0xffffffff|Prioridade relativa das extensões. Se dois ou mais idiomas compartilham a mesma extensão, a língua de maior prioridade é escolhida.|

 Além disso, a seleção padrão do usuário atual para um editor\\é armazenada em\\HKEY_Current_User\Software\Microsoft\VisualStudio*X.Y*\Editores padrão*ext*. O GUID do serviço de idioma selecionado está na entrada Personalizada. Isso tem precedência para o usuário atual.

### <a name="example"></a>Exemplo

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      Extensions\
       (Default) = reg_sz:
       *         = reg_dword:0x00000018
       html      = reg_dword:0x00000027
       shtm      = reg_dword:0x00000027
       shtml     = reg_dword:0x00000027
```

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Inscrições de registro para opções de serviço de idioma de framework de pacote gerenciado
 As seguintes entradas de registro são específicas para as classes de serviço de serviço de idiomas do MPF .framework de pacote gerenciado. Essas entradas de registro indicam suporte no serviço de idiomas para vários recursos do IntelliSense e para outros recursos avançados de edição.

 Essas entradas de registro <xref:Microsoft.VisualStudio.Package.LanguagePreferences> são acessadas através da classe.

|Nome|Type|Intervalo|Descrição|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0-1|Suporte para operações IntelliSense.|
|MatchBraces|REG_DWORD|0-1|Suporte para pares de idiomas correspondentes, como aparelhos, parênteses e suportes.|
|QuickInfo|REG_DWORD|0-1|Suporte para a operação Informações Rápidas do IntelliSense.|
|ShowMatchingBrace|REG_DWORD|0-1|Suporte para exibir o par de idiomas correspondente na barra de status.|
|MatchBracesAtCaret|REG_DWORD|0-1|Suporte para exibir pares de idiomas correspondentes, normalmente através do destaque dos dois elementos.|
|MaxErrorMensagens|REG_DWORD|0-n|O número máximo de erros que podem ser exibidos na janela **Lista de erros.**|
|CodeSenseDelay|REG_DWORD|0-n|O número de milissegundos para atrasar antes de começar qualquer análise de fundo para uma operação IntelliSense.|
|EnableAsyncComplet|REG_DWORD|0-1|Suporte para análise de fundo.|
|Habilitarcomentários|REG_DWORD|0-1|Suporte para comentar blocos selecionados de texto, e também implica suporte para não comentar texto selecionado.|
|HabilitarSFormatSelection|REG_DWORD|0-1|Suporte para formatação de texto, como recuo automático ou ajuste da posição dos aparelhos.|
|AutoOutlining|REG_DWORD|0-1|Apoio ao delineamento (regiões que podem ser colapsadas).|
|MaxRegiões|REG_DWORD|0-n|O número máximo de regiões ocultas por arquivo.|

```
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      XML\
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}
        MatchBraces           = reg_dword:0x00000001
        QuickInfo             = reg_dword:0x00000001
        ShowMatchingBrace     = reg_dword:0x00000001
        MatchBracesAtCaret    = reg_dword:0x00000000
        MaxErrorMessages      = reg_dword:0x00000064
        CodeSenseDelay        = reg_dword:0x000001f4
        MaxRegions            = reg_dword:0x0000000a
```

## <a name="see-also"></a>Confira também
- [Desenvolvendo um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)
