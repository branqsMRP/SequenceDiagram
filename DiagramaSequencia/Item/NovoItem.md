```mermaid
sequenceDiagram 
    % diagrama da tela de novo Item

    actor Engenheiro/Admin
    participant Sistema
    participant C as Cadastro
    participant VC as Verificador Cadastro
    participant VL as Verifica Lista
    participant LM as Lista Materiais


    Engenheiro/Admin->>Sistema: Digite as infos necessárias()
    activate Engenheiro/Admin
    activate Sistema
    Sistema->>C: inputListaItens()
    activate C
    % alterar essa parte pós desenvolvimento do diagrama de classes para colocar o comando padrão que aparece no diagrama.

    alt Cadastro de Item
        C->>VC: validar_Inserir()
        % alterar essa parte pós desenvolvimento do diagrama de classes para colocar o comando padrão que aparece no diagrama.
        activate VC
            alt Lista de Itens
            VC->>VL: validar_inserirMaterialListaMaterial()
                    % alterar essa parte pós desenvolvimento do diagrama de classes para colocar o comando padrão que aparece no diagrama.
            activate VL
            VL->>LM: ListItem()
                    % alterar essa parte pós desenvolvimento do diagrama de classes para colocar o comando padrão que aparece no diagrama.
            activate LM
            LM->>C: CadListOk()
                    % alterar essa parte pós desenvolvimento do diagrama de classes para colocar o comando padrão que aparece no diagrama.
            deactivate LM
            else Não Listagem de Items
            VL-->>C: return()
            deactivate VL
            end
    else Erro
        VC-->>C: erro:string
        deactivate VC
    end

    C->>Sistema: CadPronto()
    deactivate C
    Sistema->>Engenheiro/Admin: Cadastro feito()
    deactivate Sistema
    deactivate Engenheiro/Admin

``` 