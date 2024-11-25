Passo a passo para tentar recuperar os dados de um HD no Windows usando ferramentas disponíveis no sistema e o **Prompt de Comando (CMD)**.

---

## **Passo 1: Verificar se o Windows reconhece o HD**
1. **Conecte o HD ao computador**.
2. Pressione `Win + E` para abrir o Explorador de Arquivos e veja se o HD aparece na lista de dispositivos. 
   - Se não aparecer, continue com os passos abaixo.

---

## **Passo 2: Usar o Gerenciamento de Disco**
1. Pressione `Win + R`, digite `diskmgmt.msc` e pressione `Enter`.
2. No **Gerenciamento de Disco**, localize o HD:
   - **Se aparecer sem letra atribuída:** Clique com o botão direito e escolha **Alterar letra de unidade e caminho**. Atribua uma letra ao HD.
   - **Se aparecer como "não alocado":** O HD pode estar corrompido. Continue com as etapas abaixo.

---

## **Passo 3: Reparar o HD com o CMD**
### **3.1. Usar o comando CHKDSK**
1. Abra o CMD como administrador:
   - Pressione `Win + S`, digite `cmd`, clique com o botão direito em **Prompt de Comando** e escolha **Executar como administrador**.
2. Digite o comando:
   ```cmd
   chkdsk X: /f /r /x
   ```
   - Substitua `X:` pela letra do seu HD.
   - O comando faz uma varredura no disco, corrigindo setores defeituosos e tentando recuperar dados legíveis.
3. Aguarde o término da operação e veja se o HD aparece no Explorador de Arquivos.

---

### **3.2. Usar o comando DISKPART**
Se o HD não aparecer no Explorador, mas estiver listado no Gerenciamento de Disco:
1. No CMD, digite:
   ```cmd
   diskpart
   ```
2. Liste os discos conectados:
   ```cmd
   list disk
   ```
3. Identifique o número do disco correspondente ao seu HD (exemplo: `Disk 1`).
4. Selecione o disco:
   ```cmd
   select disk 1
   ```
5. Veja os volumes no disco:
   ```cmd
   list volume
   ```
6. Tente atribuir uma letra ao volume do HD:
   ```cmd
   assign letter=X
   ```
   - Substitua `X` pela letra que você deseja atribuir.

---

## **Passo 4: Copiar os Dados com o Robocopy**
Se o HD for reconhecido após os passos anteriores:
1. No CMD, use o **Robocopy** para copiar os dados do HD para outra pasta ou dispositivo:
   ```cmd
   robocopy X:\ C:\Backup /E
   ```
   - Substitua `X:\` pela letra do HD e `C:\Backup` pelo destino da cópia.
   - A opção `/E` copia todos os arquivos e pastas, incluindo os vazios.

---

## **Passo 5: Tentar Recuperação de Dados (Se Necessário)**
Se os passos anteriores não resolverem:
1. Use a **Recuperação de Arquivos do Windows** (Windows File Recovery):
   - Baixe o programa da Microsoft Store.
   - Abra o CMD como administrador e use o comando:
     ```cmd
     winfr X: C:\Recuperados /extensive
     ```
     - Substitua `X:` pela letra do HD e `C:\Recuperados` pelo destino dos arquivos recuperados.

2. O modo **/extensive** tenta recuperar dados de um HD corrompido.

---

## **Dicas Finais**
- Se nenhuma das etapas acima funcionar, considere usar ferramentas especializadas de terceiros, como **Recuva**, **EaseUS Data Recovery**, ou **Disk Drill**.
- Evite gravar novos dados no HD para não sobrescrever os arquivos que ainda podem ser recuperados.
