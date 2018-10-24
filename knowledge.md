### 合并第一列中相同名字的列
    jQuery.fn.rowspan = function(colIdx) {
        return this.each(function(){
            var that;
            $('tr', this).each(function(row) {
                $('td:eq('+colIdx+')', this).filter(':visible').each(function(col) {
                    if (that!=null && $(this).find("span").text() == $(that).find("span").text()) { //判断相等条件
                        rowspan = $(that).attr("rowSpan");
                        if (rowspan == undefined) {
                            $(that).attr("rowSpan",1);
                            rowspan = $(that).attr("rowSpan"); }
                        rowspan = Number(rowspan)+1;
                        $(that).attr("rowSpan",rowspan);
                        $(this).hide();
                    } else {
                        that = this;
                    }
                });
            });
        });
    }
### 