Como falamos, o lean de cash balance é todo para menu gerente, entao deve ter liberado a consulta direta por conta e se pesquisar pelo tip de documentotambem deve poder escolher o documento para selecionar a conta



Esta alteração tem que ser feita sempre, or que ela vai suportar cliente e gerente para a nrpe005 que pesquisa as contas de um gerente

Primeira alteração na brpe005.model 

Acrescentar na classe disable 

export class Disabled {
    public naRelacion1: boolean = true;
    public naCerrar1: boolean = false;
    public naAceptar1: boolean = true;
    public naContrato1: boolean = true;
    public naAbandonar1: boolean = false;
   public beanpebanespa1: boolean = false;
}

Na brpe005.component.html

Colocar    [disabled]="modelBrpe005._disabled.beanpebanespa1" no campo de tipo doc e no campo N2 documento


Rememplazar o ícone de pesquisa pelo botão habilitado e deshabilitadom atualizar o id com o correspondente de cada lean

             <div class="col-xs-1 col-xs-1_width5">
                <div *ngIf="modelBrpe005._disabled.beanpebanespa1">
                    <div id="btn-psct-brpe005-beanpebanespa-1"
                        style="margin-top: 20px; margin-left: -10px; padding-left: 0px; margin-right: -50px; color: #c2c2c2">
                        <em class="icon-pesquisar icon-24"></em>
                    </div>
                </div>
                <div *ngIf="!modelBrpe005._disabled.beanpebanespa1">
                    <div id="btn-psct-brpe005-beanpebanespa-1"
                        style="cursor:pointer; margin-top: 20px; margin-left: -10px; padding-left: 0px; margin-right: -50px "
                        (click)="beanpebanespa1ButtonClick()">
                        <em class="icon-pesquisar icon-24"></em>
                    </div>
                </div>
             </div>




No brpe005.component.ts

Dentro do context  substituir pelo seguinte código

                                                                                              if (context.basicData && context.basicData.document) {
                                                                                                              this.modelBrpe005.tipdoc.value = context.basicData.document.type;
                                                                                                              this.modelBrpe005.penumdo = context.basicData.document.number;
                                                                                              }
                                                                                              if (context.basicData && context.basicData.person) {
                                                                                                              this.modelBrpe005.penompe = context.basicData.person.name;
                                                                                                              this.modelBrpe005.penumpe = context.basicData.person.personCode;
                                                                                              }

E antes do loaderservice.show (no ngonint) colocar

                if (this.modelBrpe005.penumpe.trim())  {
                    this.modelBrpe005._disabled.beanpebanespa1 = true;
                }

Att
