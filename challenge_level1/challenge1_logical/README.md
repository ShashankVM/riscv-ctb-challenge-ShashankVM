## Bug: Invalid generated assembly operands
1. test.S:15855: Error: illegal operands `and s7,ra,z4' 
   The register z4 is invalid source register.
2. test.S:25584: Error: illegal operands `andi s5,t1,s0'
   The operand s0 is illegal in this context, it needs to be an immediate operand.    
![Before the fix: generated assembly contains an invalid register and an immediate instruction with a register operand](image-2.png)

## Fix
![After the fix: the invalid register and immediate operand are corrected](image-1.png)

## Explanation
1. test.S:15855: Error: illegal operands `and s7,ra,z4' 
   The register name z4 is invalid source register name, replaced it with s4.
2. test.S:25584: Error: illegal operands `andi s5,t1,s0'
   The operand s0 is illegal in this context, it needs to be an immediate operand. Replaced it with 0.  