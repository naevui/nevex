# Nevex

Nevex, sıfırdan tasarlanmış register-based bir komut seti mimarisi (ISA) ile bu ISA için bir sanal makine, bir assembler ve ileride C-benzeri küçük bir dil için compiler içeren projedir. Uzun vadeli hedef, ISA'yı gerçek donanıma (FPGA) taşımak ve üzerinde basit bir işletim sistemi çalıştırmaktır.

[English](README.md)

> Proje ilk olarak "Vex" adıyla planlandı. VexRiscv ve HP VEX ISA ile isim çakışması nedeniyle "Nevex" olarak değiştirildi.

## Neden

Çoğu hobi VM'i stack tabanlı bir makineyle kalıyor. Nevex, RISC-V ve ARM'ın tasarım felsefesine yakın bir register mimarisi seçiyor. Böylece aynı spesifikasyon sonradan yeniden tasarlanmadan donanımda uygulanabilir. ISA tasarım kararlarını önce VM'de, sonra donanımda denemek için bir deney zemini olarak düşünülmüştür.

## Tasarım kısıtları

- **Register-based**, RISC-V/ARM tarzı, stack-based değil.
- **Flat bellek.** MMU ve sanal bellek yok.
- **İki ayrıcalık seviyesi:** user mode ve kernel mode, bunun ötesi yok.

Kısıtlar bilinçli: mimari minimal tutuluyor ki VM ve ileride FPGA implementasyonu birebir aynı davransın.

## Bileşenler

| Bileşen | Kaynak | Durum |
|---|---|---|
| ISA spesifikasyonu | `ISA.md`, `isa.h` | Repoda |
| Sanal makine (C) | `nevex.c` | Repoda |
| Assembler | `nevexas.c` | Repoda |
| Compiler (C-benzeri dil) | henüz yok | Planlanıyor |
| Nevex OS | henüz yok | Planlanıyor |
| FPGA implementasyonu (Verilog/VHDL) | henüz yok | Planlanıyor |

`nevexas.asm` örnek bir assembly programıdır, `examples/` altında başka programlar vardır.

## Derleme

```sh
git clone https://github.com/naevui/nevex.git
cd nevex
make
```

## Yol haritası

1. ISA spesifikasyonunu sabitle (register sayısı, instruction formatları, opcode tablosu)
2. VM: fetch-decode-execute döngüsü
3. Assembler
4. C-benzeri küçük dil için compiler
5. Nevex OS: user/kernel ayrımı, temel syscall arayüzü
6. FPGA'ya taşıma

## Katkıda bulunma

Proje erken aşamada. ISA tasarımı ve mimari kararlar üzerine issue ve tartışmalar memnuniyetle karşılanır.

## Lisans

Henüz seçilmedi. Projenin açık kaynak olması planlanıyor.
