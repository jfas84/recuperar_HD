Kali Linux, existem várias ferramentas avançadas para recuperação de dados. Uma das mais utilizadas é o **TestDisk**, que é poderosa e gratuita, capaz de recuperar partições perdidas e restaurar discos danificados.

---

### **Passo a Passo para Recuperar Dados com o TestDisk no Kali Linux**

#### **1. Instalar o TestDisk**
Se o TestDisk não estiver instalado, você pode instalá-lo:
1. Abra o terminal.
2. Execute o comando:
   ```bash
   sudo apt update && sudo apt install testdisk
   ```

---

#### **2. Identificar o Disco**
1. Liste os discos conectados ao sistema:
   ```bash
   sudo fdisk -l
   ```
2. Identifique o disco ou a partição do HD que deseja recuperar (exemplo: `/dev/sdb`).

---

#### **3. Executar o TestDisk**
1. No terminal, inicie o TestDisk:
   ```bash
   sudo testdisk
   ```
2. Siga as etapas no menu interativo:
   - Escolha **Create** para criar um novo arquivo de log.
   - Selecione o HD ou dispositivo que deseja recuperar usando as teclas de direção.
   - Escolha o tipo de tabela de partição:
     - Geralmente, **Intel** para discos MBR ou **EFI GPT** para discos GPT.

---

#### **4. Analisar o Disco**
1. Escolha **Analyse** e pressione `Enter`:
   - O TestDisk irá buscar partições perdidas ou danificadas.
2. Selecione **Quick Search** para uma análise rápida:
   - Se o disco ou partição perdida aparecer, selecione-a e continue para recuperação.
   - Caso não funcione, escolha **Deeper Search** para uma análise mais detalhada.

---

#### **5. Recuperar Partições**
1. Após encontrar partições perdidas:
   - Use as teclas para selecionar a partição desejada.
   - Escolha **Write** para restaurar a tabela de partições e pressione `Enter`.
   - Confirme escrevendo as alterações.

---

#### **6. Recuperar Arquivos Específicos**
Se desejar recuperar arquivos sem restaurar a partição:
1. Escolha **Advanced** no menu principal.
2. Selecione a partição onde os arquivos estão.
3. Escolha **Undelete**:
   - Navegue pelos arquivos e selecione os desejados com as setas do teclado.
   - Pressione `C` para copiar os arquivos para um local seguro.
4. Escolha o destino no sistema onde deseja salvar os arquivos recuperados.

---

#### **7. Salvar os Arquivos Recuperados**
- Durante o processo de cópia, selecione um diretório seguro, como um HD externo ou um outro disco no sistema.

---

### **Dicas Adicionais**
- **Evite sobrescrever dados:** Não grave arquivos novos no HD danificado antes de recuperar os dados.
- **Tenha cuidado com discos críticos:** Para discos muito danificados, usar o `ddrescue` antes do TestDisk pode ajudar a criar uma imagem do disco para evitar perdas adicionais.
- Para arquivos excluídos, o **Photorec**, que vem junto com o TestDisk, pode ser usado para recuperação aprofundada de arquivos por assinatura.
