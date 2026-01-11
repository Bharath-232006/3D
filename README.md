# 3D
Dataflow Description

module comp (a,b, agtb, aeqb, alsb); 
input a; input b; 
output agtb; output aeqb; output alsb; 
assign agtb = a&(~b); 
assign alsb = (~a)&b; 
assign aeqb = ~(a^b); 
endmodule

Behavioral Description

module comparator (a,b,y); 
input a; input b; 
output [2:0]y; 
reg[2:0]y; 
wire[1:0]sel; 
assign sel={a,b}; 
always @(sel)begin case(sel)
 2'd0: y = 3'd2; 
2'd1: y = 3'd1; 
2'd2: y = 3'd4;
 2'd3: y = 3'd2; 
endcase 
end 
endmodule

Structural Description

module comparator
 (a,b,agtb,aeqb,alsb); 
input a; input b; 
output agtb; 
output aeqb;
output alsb; 
wire x,y; 
not u1(x,a); 
not u2(y,b); 
and u3(agtb,a,y);
 xnor u4(aeqb,a,b);
 and u5(alsb,x,b);
 endmodule
