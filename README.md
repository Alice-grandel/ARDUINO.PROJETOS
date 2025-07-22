<h1 align="center">🧬🚀 Arduino com Rust — Projeto Experimental</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Rust🦀-Low%20Level-orange?style=flat-square" />
  
  <img src="https://img.shields.io/badge/Arduino⚡-Hardware-blue?style=flat-square" />
  <img src="https://img.shields.io/badge/Autodidata📚-Em%20progresso-green?style=flat-square" />
</p>

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/8/87/Arduino_Logo.svg" height="100" alt="Arduino Logo"/>
  &nbsp;&nbsp;&nbsp;&nbsp;
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/20/Rustacean-orig-noshadow.svg/320px-Rustacean-orig-noshadow.svg.png" width="150" alt="Rustacean" title="Rust" />

</p>

---

## 🌟 Sobre o projeto

Este repositório é uma coleção dos meus experimentos usando **Rust** com **Arduino** — Ainda não sei se quero trabalhar com embarcados, mas eu quero:

> **Aprender algo difícil, diferente e me tornar uma desenvolvedora melhor.**  
> E isso aqui é diferente de tudo que já fiz. 💡

---

## 🎯 Objetivos

- ✅ Praticar **Rust** em contexto de sistemas embarcados
- ✅ Aprender a lidar com **hardware real** e entender como tudo funciona "de verdade"
- ✅ Enriquecer meu GitHub com um projeto técnico, ousado e fora da curva
- ✅ Traduzir conceitos da eletrônica para lógica de programação e vice-versa

---

## 🛠️ Tecnologias e ferramentas

| Tecnologia | Descrição |
|------------|-----------|
| 🦀 **Rust** | Linguagem moderna, segura e poderosa para sistemas de baixo nível |
| ⚡ **Arduino ARM/STM32F103C6T6** | Microcontroladores usados nos testes |
| 🧠 **VS Code / Rust Analyzer** | Ambientes de desenvolvimento |
| 🔧 **ARMR-Rust / Cargo / Probe-rs** | Ferramentas de compilação e upload |
| 🔍 **Datasheets & referências técnicas** | Estudo direto nos registradores e esquemáticos |

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/8/87/Arduino_Logo.svg" height="100" alt="Arduino Logo"/>
  &nbsp;&nbsp;&nbsp;&nbsp;
  <img src="https://upload.wikimedia.org/wikipedia/commons/d/d5/Rust_programming_language_black_logo.svg" height="100" alt="Rust Logo"/>
</p>

## 📘 Documentação e tutoriais
- [The Embedded Rust Book](https://docs.rust-embedded.org/book/)
- [Documentação oficial rust](https://rust-br.github.io/rust-book-pt-br/ch04-01-what-is-ownership.html/)
- [Rust para sistemas embarcados (YouTube)](https://www.youtube.com/watch?v=QH10Be79zPA&t=15s)
- [Rust Embedded Working Group](https://github.com/rust-embedded)
- [Rust Programming Notebook (recurso complementar)](https://github.com/rust-lang/book)
---

## 📦 Meu Kit
- [Kit Arduino UNO (Amazon)](https://www.amazon.com.br/dp/B0DB8XP6RS?ref=ppx_yo2ov_dt_b_fed_asin_title)
- [Placa ARM STM32 "Blue Pill" (Amazon)](https://www.amazon.com.br/dp/B0C3SMXP8H?ref=ppx_yo2ov_dt_b_fed_asin_title)
- [SOLDAR BARRAS DE PINOS DO ARDUINO ARM: (YouTube)](https://www.youtube.com/shorts/EhAbcc_Fgtc?feature=share)

---

## 📚 O que estou estudando

- Fundamentos de **Rust embarcado**
- Projetos e crates como `embedded-hal`, `avr-device` e `panic-halt`
- Lógica digital aplicada em código
- Datasheets dos chips AVR e ARM

---

## ✅ Conquistas até agora

- 💡 LED piscando com Rust
- 🔌 Comunicação serial com `avr-hal`
- ⚙️ Manipulação de registradores com segurança
- 🔧 Setup funcional com Rust e Arduino

---

## 🔮 Próximos passos

- 📈 PWM e Timers com `embedded-hal`
- 📡 Comunicação via I2C/SPI
- 🧠 Controle de sensores simples com Rust
- 🧪 Testes com atuadores e pequenos módulos

---
# Projeto STM32F103C6T6 em Rust

Este projeto é um exemplo básico de como fazer o LED da placa piscar.
![arduino](https://github.com/user-attachments/assets/7d62064f-b86c-446b-b7bd-b0b680b6832f)


## CÓDIGO PRINCIPAL PISCAR LED:

```rust
#![no_std]
#![no_main]

use cortex_m_rt::entry;
use panic_halt as _;

use stm32f1xx_hal::{delay::Delay, flash::FlashExt, gpio::GpioExt, pac, rcc::RccExt};

use embedded_hal::blocking::delay::DelayMs;
use embedded_hal::digital::v2::OutputPin;

#[entry]
fn main() -> ! {
    let dp = pac::Peripherals::take().unwrap();
    let cp = pac::CorePeripherals::take().unwrap();

    let mut flash = dp.FLASH.constrain();
    let mut rcc = dp.RCC.constrain();
    let clocks = rcc.cfgr.freeze(&mut flash.acr);

    let mut gpioa = dp.GPIOA.split(&mut rcc.apb2);
    let mut led = gpioa.pa0.into_push_pull_output(&mut gpioa.crl);

    let mut delay = Delay::new(cp.SYST, clocks);

    loop {
        // Usando os nomes de método corretos.
        led.set_high().unwrap();
        delay.delay_ms(500_u16);
        led.set_low().unwrap();
        delay.delay_ms(500_u16);
    }
}


```
---
## ✨ Sobre mim

Sou uma desenvolvedora iniciante, apaixonada por desafios técnicos, que aprende rápido e gosta de sair da zona de conforto. Este projeto é uma forma de mostrar:

> Que mesmo sem conteúdo pronto, eu aprendo, adapto, testo, erro e **faço acontecer**.

---

### 💬 Fique à vontade para explorar os códigos que virão aqui em breve!

<p align="center">
  Feito com 💜 por <strong>Alice Grandel</strong>
</p>
