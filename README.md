## 🛠️ **Conversores AD - BitDogLab**

Este projeto implementa o controle de **Conversores Analógico-Digitais (ADC)** no **RP2040**, utilizando a **placa BitDogLab**. Ele inclui a leitura de valores de um **joystick analógico**, controle de **LEDs RGB via PWM**, e a exibição das leituras em um **display OLED SSD1306**.

## 📹 **Demonstração**
🔗 **Vídeo da demonstração**: [Youtube](https://youtu.be/avltHM8HlMw)

---

## 📌 **Objetivos**
✔️ **Compreender** o funcionamento do **Conversor Analógico-Digital (ADC)** no **RP2040**  
✔️ **Utilizar o PWM** para controlar a **intensidade dos LEDs RGB** com base no **joystick**  
✔️ **Representar a posição do joystick** em um **display OLED SSD1306** através de um **quadrado móvel**  
✔️ **Aplicar o protocolo I2C** na comunicação com o **display**  
✔️ **Implementar interrupções** para detecção de **botões físicos**  

---

## 📦 **Estrutura do Projeto**
```
/conversores-ad
│── build/                      # Diretório de build
│── includes/                    # Arquivos de cabeçalho (Headers)
│   │── adc.h                    # Leitura dos valores ADC
│   │── display.h                 # Controle do display OLED
│   │── entradas.h                # Interrupções dos botões físicos
│   │── font.h                    # Fonte para o display
│   │── leds.h                    # Controle dos LEDs RGB
│   │── pwm.h                     # Configuração do PWM
│   │── ssd1306.h                 # Driver do display SSD1306
│── src/                         # Implementação dos módulos
│   │── adc.c                     # Implementação da leitura ADC
│   │── display.c                 # Implementação do display
│   │── entradas.c                # Implementação das interrupções
│   │── leds.c                    # Implementação do controle dos LEDs
│   │── pwm.c                     # Implementação do PWM
│   │── ssd1306.c                 # Implementação do driver SSD1306
│── CMakeLists.txt                # Configuração do CMake
│── conversores-ad.c              # Arquivo principal
│── pico_sdk_import.cmake         # Configuração do Pico SDK
│── README.md                     # Documentação do projeto
│── wokwi.toml                    # Configuração para simulação no Wokwi
```

---

## ⚙️ **Pré-requisitos**
Para compilar e executar o projeto, é necessário ter instalado:
- [Pico SDK](https://github.com/raspberrypi/pico-sdk)
- [CMake](https://cmake.org/download/)

### 📌 **Clonando o Repositório**
```bash
git clone https://github.com/brenotainandev/conversores-ad.git
cd conversores-ad
```

---

## 🚀 **Instalação e Execução**
### **1️⃣ Configurar o ambiente do Pico SDK**
```bash
export PICO_SDK_PATH=../pico-sdk
```

### **2️⃣ Criar o diretório de build e compilar**
```bash
mkdir build && cd build
cmake ..
ninja
```

### **3️⃣ Enviar o binário para o Raspberry Pi Pico**
- Conecte o **Raspberry Pi Pico** segurando o botão `BOOTSEL`
- Copie o arquivo `.uf2` gerado para a unidade montada do Pico
```bash
cp conversores-ad.uf2 /media/$USER/RPI-RP2/
```

---

## 📂 **Módulos e Arquitetura**
O código está **modularizado** para facilitar a manutenção e reutilização. Aqui está um resumo dos principais arquivos:

### 🔹 `conversores-ad.c`
> **Função principal do projeto**, inicializa os módulos e gerencia o loop principal.

### 🔹 `adc.c / adc.h`
> **Gerencia a leitura dos valores analógicos do joystick** via **ADC**.

### 🔹 `entradas.c / entradas.h`
> **Gerencia os botões físicos** com **interrupções (IRQ)**.

### 🔹 `leds.c / leds.h`
> **Controla os LEDs RGB** utilizando **PWM**, variando a intensidade conforme os valores do joystick.

### 🔹 `pwm.c / pwm.h`
> **Configura e altera o estado do PWM** para os LEDs.

### 🔹 `display.c / display.h`
> **Gerencia a exibição no display OLED**, incluindo movimentação do quadrado.

### 🔹 `ssd1306.c / ssd1306.h`
> **Driver do display OLED SSD1306**, utilizando **protocolo I2C**.

---

## 📌 **Funcionalidades**
✔️ **Leitura do joystick analógico** via **ADC** (GPIOs 26 e 27)  
✔️ **Controle dos LEDs RGB** conforme a posição do joystick  
✔️ **Movimentação de um quadrado** no **display OLED SSD1306**  
✔️ **Uso de PWM** para variação de brilho dos LEDs  
✔️ **Interrupções para botões** físicos (**debouncing implementado**)  
✔️ **Alternar estados do LED Verde** e **borda do display** ao pressionar o botão do joystick  
✔️ **Ativar/desativar os LEDs PWM** ao pressionar o botão A  

---

## 📜 **Requisitos do Projeto**
✅ **Uso de interrupções**: Todas as funcionalidades dos botões foram implementadas com **IRQ**  
✅ **Debouncing implementado**: Prevenção de múltiplos acionamentos ao pressionar os botões  
✅ **Utilização do display SSD1306**: Exibição de um **quadrado móvel** para representar o joystick  
✅ **Código bem estruturado**: **Modularização** para fácil manutenção  

### **Hardware Utilizado**
- **Raspberry Pi Pico**
- **Joystick analógico** (GPIOs 26 e 27)
- **Botão A** (GPIO 5)
- **Botão do Joystick** (GPIO 22)
- **LED RGB** (GPIOs 11, 12 e 13)
- **Display OLED SSD1306** (I2C - GPIOs 14 e 15)

---

## 📚 **Referências**
- **Pico SDK:** [https://github.com/raspberrypi/pico-sdk](https://github.com/raspberrypi/pico-sdk)

## 📜 Licença

Este projeto é de **uso educacional** e segue a licença MIT. Sinta-se à vontade para modificá-lo e contribuir!