<xml xmlns="http://www.w3.org/1999/xhtml" collection="false">
  <variables>
    <variable type="" id="d*Xs0XxB.g9IS(s/7Uo(">buymode</variable>
    <variable type="" id="/_wANg-@3LwCams(mM:8">stake</variable>
    <variable type="" id="]O.omd!Iq4H@$}.-]mv5">initial stake</variable>
    <variable type="" id="r2e=8=P7)DFSOZwP_xPT">counter</variable>
    <variable type="" id="runCounter">runCounter</variable> <!-- New variable for the run count -->
  </variables>
  <block type="trade" id="xgH69|xFn9=70w.*3Vo@" x="86" y="-66">
    <field name="MARKET_LIST">synthetic_index</field>
    <field name="SUBMARKET_LIST">random_daily</field>
    <field name="SYMBOL_LIST">RDBEAR</field>
    <field name="TRADETYPECAT_LIST">digits</field>
    <field name="TRADETYPE_LIST">evenodd</field>
    <field name="TYPE_LIST">both</field>
    <field name="CANDLEINTERVAL_LIST">60</field>
    <field name="TIME_MACHINE_ENABLED">FALSE</field>
    <field name="RESTARTONERROR">TRUE</field>
    <statement name="INITIALIZATION">
      <block type="variables_set" id="y(CvmLl|CiDbF4z+5T7]">
        <field name="VAR" id="d*Xs0XxB.g9IS(s/7Uo(" variabletype="">buymode</field>
        <value name="VALUE">
          <block type="logic_boolean" id="{[;V9^ubbT`xg,-W_XIz">
            <field name="BOOL">FALSE</field>
          </block>
        </value>
        <next>
          <block type="variables_set" id="2|X@GJp%DEQ?hvmzQs3$">
            <field name="VAR" id="]O.omd!Iq4H@$}.-]mv5" variabletype="">initial stake</field>
            <value name="VALUE">
              <block type="math_number" id="`UmQUc/CD}jaw|4Z_P@R">
                <field name="NUM">1</field>
              </block>
            </value>
            <next>
              <block type="variables_set" id="6eWI/7(-V36,kyw,-Zz2">
                <field name="VAR" id="/_wANg-@3LwCams(mM:8" variabletype="">stake</field>
                <value name="VALUE">
                  <block type="variables_get" id="]=nh;6n{$f:ab5bF4V`_">
                    <field name="VAR" id="]O.omd!Iq4H@$}.-]mv5" variabletype="">initial stake</field>
                  </block>
                </value>
              </block>
            </next>
          </block>
        </next>
      </block>
      <next>
        <block type="variables_set" id="set_run_counter">
          <field name="VAR" id="runCounter" variabletype="">runCounter</field>
          <value name="VALUE">
            <block type="math_number" id="run_initial_value">
              <field name="NUM">0</field> <!-- Initialize the run counter -->
            </block>
          </value>
        </block>
      </next>
    </statement>

    <statement name="SUBMARKET">
      <block type="tradeOptions" id="x=V33~4Lb|(sLv`J[:Eb">
        <field name="DURATIONTYPE_LIST">t</field>
        <field name="CURRENCY_LIST">USD</field>
        <field name="BARRIEROFFSETTYPE_LIST">+</field>
        <field name="SECONDBARRIEROFFSETTYPE_LIST">-</field>
        <value name="DURATION">
          <shadow type="math_number" id="aVobso]zc-3(T/LYm8xz">
            <field name="NUM">1</field>
          </shadow>
        </value>
        <value name="AMOUNT">
          <shadow type="math_number" id="ml)25~7^q}3I9}vjf:%K">
            <field name="NUM">1</field>
          </shadow>
          <block type="variables_get" id="G-@Fp^yOWkx_(yX#zZdg">
            <field name="VAR" id="/_wANg-@3LwCams(mM:8" variabletype="">stake</field>
          </block>
        </value>
      </block>
    </statement>
  </block>

  <block type="tick_analysis" id="flrgUy2Z`oQcv}Qsw*|z" x="493" y="432">
    <statement name="TICKANALYSIS_STACK">
      <block type="controls_if" id="%xRu-|8)ZkR`c9r[~=zv">
        <mutation else="1"></mutation>
        <value name="IF0">
          <block type="math_number_property" id="6J:{y7(nLK9eQW/T]li(">
            <mutation divisor_input="false"></mutation>
            <field name="PROPERTY">ODD</field>
            <value name="NUMBER_TO_CHECK">
              <shadow type="math_number" id="6)R-Zcj)z9?3.^iKP;wL">
                <field name="NUM">0</field>
              </shadow>
              <block type="tick" id="r)7;s0a~Q.wBojXjXs}?"></block>
            </value>
          </block>
        </value>
        <statement name="DO0">
          <block type="math_change" id="Z3%RpcB~z4G%1wh1ey-Q">
            <field name="VAR" id="r2e=8=P7)DFSOZwP_xPT" variabletype="">counter</field>
            <value name="DELTA">
              <shadow type="math_number" id="9jCNP{uuAd}#WDk^jb0E">
                <field name="NUM">1</field>
              </shadow>
            </value>
          </block>
        </statement>
        <statement name="ELSE">
          <block type="variables_set" id="PUMscGks1HFplvK.9f]~">
            <field name="VAR" id="r2e=8=P7)DFSOZwP_xPT" variabletype="">counter</field>
            <value name="VALUE">
              <block type="math_number" id="v]1/R7B6tcN=@BR|*$0u">
                <field name="NUM">0</field>
              </block>
            </value>
            <next>
              <block type="notify" id="GBsVAn[Bjm[mYkHc8A]Q">
                <field name="NOTIFICATION_TYPE">success</field>
                <field name="NOTIFICATION_SOUND">silent</field>
                <value name="MESSAGE">
                  <shadow type="text" id="?z31WH:5uZ*AAB.(`@Sz">
                    <field name="TEXT">nope</field>
                  </shadow>
                </value>
              </block>
            </next>
          </block>
        </statement>
        <next>
          <block type="math_change" id="increment_run_counter">
            <field name="VAR" id="runCounter" variabletype="">runCounter</field>
            <value name="DELTA">
              <shadow type="math_number" id="increment_by_1">
                <field name="NUM">1</field>
              </shadow>
            </value>
            <next>
              <block type="controls_if" id="check_100_runs">
                <value name="IF0">
                  <block type="logic_compare" id="check_run_counter">
                    <field name="OP">GTE</field>
                    <value name="A">
                      <block type="variables_get" id="run_counter_value">
                        <field name="VAR" id="runCounter" variabletype="">runCounter</field>
                      </block>
                    </value>
                    <value name="B">
                      <block type="math_number" id="limit_to_100">
                        <field name="NUM">100</field>
                      </block>
                    </value>
                  </block>
                </value>
                <statement name="DO0">
                  <block type
